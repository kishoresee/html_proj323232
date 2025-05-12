<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Book Management - Update & Delete</title>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet" />

  <!-- SharePoint JSOM + People Picker Scripts -->
  <script type="text/javascript" src="/_layouts/15/sp.runtime.js"></script>
  <script type="text/javascript" src="/_layouts/15/sp.js"></script>
  <script type="text/javascript" src="/_layouts/15/clienttemplates.js"></script>
  <script type="text/javascript" src="/_layouts/15/clientforms.js"></script>
  <script type="text/javascript" src="/_layouts/15/clientpeoplepicker.js"></script>
  <script type="text/javascript" src="/_layouts/15/autofill.js"></script>
</head>
<body class="bg-light p-4">
  <div class="container">
    <h2 class="mb-4 text-center text-primary">Book Management</h2>

    <div class="table-responsive mb-5">
      <table class="table table-bordered table-striped text-center" id="bookTable">
        <thead class="table-dark">
          <tr>
            <th>Actions</th>
            <th>Book Name</th>
            <th>Publication Date</th>
            <th>Author</th>
            <th>ISBN</th>
          </tr>
        </thead>
        <tbody class="table-group-divider"></tbody>
      </table>
    </div>

    <div class="card shadow">
      <div class="card-header bg-primary text-white">
        <h4 class="mb-0">Update Book Details</h4>
      </div>
      <div class="card-body">
        <div class="row g-3">
          <div class="col-md-6">
            <label for="bookName" class="form-label">Book Name</label>
            <input type="text" id="bookName" class="form-control" />
          </div>
          <div class="col-md-6">
            <label for="pubDate" class="form-label">Publication Date</label>
            <input type="date" id="pubDate" class="form-control" />
          </div>
          <div class="col-md-6">
            <label for="peoplePickerAuthor" class="form-label">Author (People Picker)</label>
            <div id="peoplePickerAuthor"></div>
          </div>
          <div class="col-md-6">
            <label for="isbn" class="form-label">ISBN</label>
            <input type="text" id="isbn" class="form-control" />
          </div>
        </div>
        <input type="hidden" id="itemId" />
        <div class="mt-4 text-end">
          <button class="btn btn-success" onclick="updateItem()">Update Book</button>
        </div>
      </div>
    </div>
  </div>

  <script type="text/javascript">
    ExecuteOrDelayUntilScriptLoaded(function () {
      initializePeoplePicker("peoplePickerAuthor");
      loadItems();
    }, "sp.js");

    function initializePeoplePicker(peoplePickerElementId) {
      var schema = {};
      schema['PrincipalAccountType'] = 'User,DL,SecGroup,SPGroup';
      schema['SearchPrincipalSource'] = 15;
      schema['ResolvePrincipalSource'] = 15;
      schema['AllowMultipleValues'] = false;
      schema['MaximumEntitySuggestions'] = 50;
      schema['Width'] = '100%';
      SPClientPeoplePicker_InitStandaloneControlWrapper(peoplePickerElementId, null, schema);
    }

    function getUserLoginFromPeoplePicker() {
      var peoplePicker = SPClientPeoplePicker.SPClientPeoplePickerDict.peoplePickerAuthor_TopSpan;
      if (!peoplePicker || peoplePicker.GetAllUserInfo().length === 0) return null;
      return peoplePicker.GetAllUserInfo()[0].Key;
    }

    function loadItems() {
      var ctx = SP.ClientContext.get_current();
      var list = ctx.get_web().get_lists().getByTitle("Book Management");
      var query = new SP.CamlQuery();
      var items = list.getItems(query);

      ctx.load(items, 'Include(Id, BookName, ISBN, PublicationDate, AuthorName)');
      ctx.executeQueryAsync(function () {
        var tbody = document.querySelector("#bookTable tbody");
        tbody.innerHTML = "";
        var enumerator = items.getEnumerator();

        while (enumerator.moveNext()) {
          var item = enumerator.get_current();
          var id = item.get_id();
          var name = item.get_item("BookName");
          var isbn = item.get_item("ISBN");
          var pubDate = item.get_item("PublicationDate");
          var author = item.get_item("AuthorName");
          var authorName = author ? author.get_lookupValue() : "";

          var formattedDate = pubDate ? new Date(pubDate).toISOString().split("T")[0] : "";

          var row = `
            <tr>
              <td>
                <button class="btn btn-sm btn-outline-primary" onclick="editItem(${id})">Select</button>
                <button class="btn btn-sm btn-outline-danger ms-2" onclick="deleteItem(${id})">Delete</button>
              </td>
              <td>${name}</td>
              <td>${formattedDate}</td>
              <td>${authorName}</td>
              <td>${isbn}</td>
            </tr>`;
          tbody.innerHTML += row;
        }
      }, onQueryFail);
    }

    function editItem(id) {
      var ctx = new SP.ClientContext.get_current();
      var list = ctx.get_web().get_lists().getByTitle("Book Management");
      var item = list.getItemById(id);

      ctx.load(item, 'BookName, ISBN, PublicationDate, AuthorName');
      ctx.executeQueryAsync(function () {
        document.getElementById("itemId").value = id;
        document.getElementById("bookName").value = item.get_item("BookName");
        document.getElementById("isbn").value = item.get_item("ISBN");

        var pubDate = item.get_item("PublicationDate");
        document.getElementById("pubDate").value = pubDate ? new Date(pubDate).toISOString().split("T")[0] : "";

        document.getElementById("peoplePickerAuthor").innerHTML = "";
        initializePeoplePicker("peoplePickerAuthor");

        setTimeout(() => {
          var author = item.get_item("AuthorName");
          if (author) {
            var picker = SPClientPeoplePicker.SPClientPeoplePickerDict.peoplePickerAuthor_TopSpan;
            picker.AddUserKeys(author.get_lookupValue());
          }
        }, 500);
      }, onQueryFail);
    }

    function updateItem() {
      var id = document.getElementById("itemId").value;
      var bookName = document.getElementById("bookName").value.trim();
      var isbn = document.getElementById("isbn").value.trim();
      var pubDate = document.getElementById("pubDate").value;
      var authorLogin = getUserLoginFromPeoplePicker();

      if (!id || !bookName || !isbn || !pubDate || !authorLogin) {
        alert("All fields are required, including selecting an Author.");
        return;
      }

      var ctx = new SP.ClientContext.get_current();
      var web = ctx.get_web();
      var list = web.get_lists().getByTitle("Book Management");
      var item = list.getItemById(id);
      var user = web.ensureUser(authorLogin);

      ctx.load(user);
      ctx.executeQueryAsync(function () {
        var userVal = new SP.FieldUserValue();
        userVal.set_lookupId(user.get_id());

        item.set_item("BookName", bookName);
        item.set_item("ISBN", isbn);
        item.set_item("PublicationDate", new Date(pubDate));
        item.set_item("AuthorName", userVal);

        item.update();
        ctx.executeQueryAsync(function () {
          alert("Book updated successfully.");
          loadItems();
          // Clear form
          document.getElementById("itemId").value = "";
          document.getElementById("bookName").value = "";
          document.getElementById("isbn").value = "";
          document.getElementById("pubDate").value = "";
          document.getElementById("peoplePickerAuthor").innerHTML = "";
          initializePeoplePicker("peoplePickerAuthor");
        }, onQueryFail);
      }, onQueryFail);
    }

    function deleteItem(id) {
      if (!confirm("Are you sure you want to delete this book?")) return;

      var ctx = new SP.ClientContext.get_current();
      var list = ctx.get_web().get_lists().getByTitle("Book Management");
      var item = list.getItemById(id);

      item.deleteObject();
      ctx.executeQueryAsync(function () {
        alert("Book deleted successfully.");
        loadItems();
      }, onQueryFail);
    }

    function onQueryFail(sender, args) {
      alert("Error: " + args.get_message());
      console.error(args.get_message());
      console.error(args.get_stackTrace());
    }
  </script>
</body>
</html>

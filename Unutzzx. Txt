<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Library Management System - Unit Test Cases</title>
  <style>
    body {
      font-family: Arial, sans-serif;
    }
    table {
      border-collapse: collapse;
      width: 100%;
      margin-bottom: 30px;
    }
    th, td {
      border: 1px solid #999;
      padding: 8px;
      text-align: left;
    }
    th {
      background-color: #f2f2f2;
    }
  </style>
</head>
<body>

<h2>Unit Test Case Document - Library Management System (LMS)</h2>

<table>
  <thead>
    <tr>
      <th>Requirement ID</th>
      <th>Test Case ID</th>
      <th>Test Case Description</th>
      <th>Step ID</th>
      <th>Test Step Description</th>
      <th>Expected Result</th>
      <th>Status</th>
      <th>Screenshot</th>
    </tr>
  </thead>
  <tbody>
    <!-- TC001: Dashboard loading -->
    <tr>
      <td rowspan="4">LMS-TASK3</td>
      <td rowspan="4">TC001</td>
      <td rowspan="4">Verify that the dashboard loads from Site Assets and renders in a Content Editor Web Part.</td>
      <td>1</td>
      <td>Upload the HTML file to the Site Assets library.</td>
      <td>HTML file is uploaded successfully without errors.</td>
      <td></td><td></td>
    </tr>
    <tr><td>2</td><td>Link it in Content Editor Web Part.</td><td>Dashboard loads correctly.</td><td></td><td></td></tr>
    <tr><td>3</td><td>Ensure sidebar is visible.</td><td>Book, Member, and Issuance menus appear.</td><td></td><td></td></tr>
    <tr><td>4</td><td>Check stats display.</td><td>Borrowed and available book counts show correctly.</td><td></td><td></td></tr>

    <!-- TC002: Add Book -->
    <tr>
      <td rowspan="5">LMS-TASK3</td>
      <td rowspan="5">TC002</td>
      <td rowspan="5">Validate Add Book functionality in Book Management.</td>
      <td>1</td><td>Click “Add New Book”.</td><td>Form appears.</td><td></td><td></td>
    </tr>
    <tr><td>2</td><td>Fill in all fields.</td><td>Form accepts values.</td><td></td><td></td></tr>
    <tr><td>3</td><td>Click Submit.</td><td>Book appears on dashboard.</td><td></td><td></td></tr>
    <tr><td>4</td><td>Try submitting empty form.</td><td>Validation blocks submission.</td><td></td><td></td></tr>
    <tr><td>5</td><td>Check DOM.</td><td>Book card is visible.</td><td></td><td></td></tr>

    <!-- TC003: Member Management -->
    <tr>
      <td rowspan="4">LMS-TASK3</td>
      <td rowspan="4">TC003</td>
      <td rowspan="4">Verify Add and Search Member functionality.</td>
      <td>1</td><td>Click “Add Member”.</td><td>Form appears.</td><td></td><td></td>
    </tr>
    <tr><td>2</td><td>Submit valid details.</td><td>Member is created.</td><td></td><td></td></tr>
    <tr><td>3</td><td>Search by name or ID.</td><td>Matching member appears.</td><td></td><td></td></tr>
    <tr><td>4</td><td>Search invalid ID.</td><td>No results or error message shown.</td><td></td><td></td></tr>

    <!-- TC004: Book Issuance -->
    <tr>
      <td rowspan="3">LMS-TASK3</td>
      <td rowspan="3">TC004</td>
      <td rowspan="3">Validate book issuance and return flow.</td>
      <td>1</td><td>Issue a book.</td><td>Status becomes “Issued”.</td><td></td><td></td>
    </tr>
    <tr><td>2</td><td>Return the book.</td><td>Status changes to “Returned”.</td><td></td><td></td></tr>
    <tr><td>3</td><td>Reissue before return.</td><td>System blocks duplicate issuance.</td><td></td><td></td></tr>

    <!-- TC005: Overdue & Notification -->
    <tr>
      <td rowspan="3">LMS-TASK3</td>
      <td rowspan="3">TC005</td>
      <td rowspan="3">Track overdue books and verify notification logic.</td>
      <td>1</td><td>Set past due date for a book.</td><td>Book marked as overdue.</td><td></td><td></td>
    </tr>
    <tr><td>2</td><td>Trigger notification via JSOM.</td><td>Email is sent.</td><td></td><td></td></tr>
    <tr><td>3</td><td>Check console logs.</td><td>Errors (if any) logged correctly.</td><td></td><td></td></tr>

    <!-- TC006: Book Search -->
    <tr>
      <td rowspan="4">LMS-TASK3</td>
      <td rowspan="4">TC006</td>
      <td rowspan="4">Validate Book Search using title, author, and ISBN.</td>
      <td>1</td><td>Search by title.</td><td>Exact match book appears.</td><td></td><td></td>
    </tr>
    <tr><td>2</td><td>Search by partial author.</td><td>All related books shown.</td><td></td><td></td></tr>
    <tr><td>3</td><td>Search invalid ISBN.</td><td>No records found.</td><td></td><td></td></tr>
    <tr><td>4</td><td>Leave search empty.</td><td>Returns all records or error.</td><td></td><td></td></tr>

    <!-- TC007: Form Validations -->
    <tr>
      <td rowspan="3">LMS-TASK3</td>
      <td rowspan="3">TC007</td>
      <td rowspan="3">Test all form validations and input errors.</td>
      <td>1</td><td>Leave required fields blank.</td><td>Validation prevents submission.</td><td></td><td></td>
    </tr>
    <tr><td>2</td><td>Enter invalid formats.</td><td>Error message shown.</td><td></td><td></td></tr>
    <tr><td>3</td><td>Use special characters.</td><td>System sanitizes or blocks input.</td><td></td><td></td></tr>

    <!-- TC008: Responsive Layout -->
    <tr>
      <td rowspan="2">LMS-TASK3</td>
      <td rowspan="2">TC008</td>
      <td rowspan="2">Test responsive layout on different screen sizes.</td>
      <td>1</td><td>View on desktop.</td><td>UI is aligned and accessible.</td><td></td><td></td>
    </tr>
    <tr><td>2</td><td>View on mobile or emulator.</td><td>Navigation collapses and works correctly.</td><td></td><td></td></tr>

    <!-- TC009: JSOM Error Handling -->
    <tr>
      <td rowspan="2">LMS-TASK3</td>
      <td rowspan="2">TC009</td>
      <td rowspan="2">Ensure JSOM error handling for missing lists/fields.</td>
      <td>1</td><td>Use incorrect list name.</td><td>Console shows “list does not exist”.</td><td></td><td></td>
    </tr>
    <tr><td>2</td><td>Use wrong internal field name.</td><td>JSOM throws and logs clear error.</td><td></td><td></td></tr>
  </tbody>
</table>

</body>
</html>

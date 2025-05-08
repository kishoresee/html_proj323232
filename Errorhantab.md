<table border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; width: 100%;">
  <thead style="background-color: #f2f2f2;">
    <tr>
      <th>Error</th>
      <th>Cause</th>
      <th>Handling Tip</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>List does not exist</td>
      <td>Wrong list title</td>
      <td>Validate using <code>/_api/web/lists</code> or double-check list name in SharePoint</td>
    </tr>
    <tr>
      <td>Field name incorrect</td>
      <td>Wrong internal field name</td>
      <td>Use SharePoint <strong>internal names</strong>, not display names</td>
    </tr>
    <tr>
      <td>Unauthorized</td>
      <td>User lacks permission</td>
      <td>Ensure user has at least <strong>Contribute</strong> permission to the list</td>
    </tr>
    <tr>
      <td>Item not found</td>
      <td>Invalid <code>itemId</code> during update/delete</td>
      <td>Add null checks or verify item existence using <code>getItemById()</code></td>
    </tr>
    <tr>
      <td>Network/timeout errors</td>
      <td>Bad internet connection or large dataset</td>
      <td>Implement retry logic or use <strong>paging</strong> in CAML queries</td>
    </tr>
  </tbody>
</table>

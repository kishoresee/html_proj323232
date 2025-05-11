<table border="1" cellpadding="10" cellspacing="0" style="border-collapse: collapse; width: 100%;">
  <thead style="background-color: #f2f2f2;">
    <tr>
      <th>Operation</th>
      <th>Error Handling Method</th>
      <th>Message or Action</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Load list items</td>
      <td><code>executeQueryAsync(..., failFn)</code></td>
      <td>Alert with failure reason</td>
    </tr>
    <tr>
      <td>Edit item</td>
      <td><code>executeQueryAsync(..., failFn)</code></td>
      <td>Alert if item can't be fetched</td>
    </tr>
    <tr>
      <td>Update item</td>
      <td><code>validateFields()</code> + <code>try-catch</code> + <code>executeQueryAsync</code></td>
      <td>Alerts for empty fields and update failure</td>
    </tr>
    <tr>
      <td>Delete item</td>
      <td><code>confirm()</code> + <code>try-catch</code> + <code>executeQueryAsync</code></td>
      <td>Confirmation + error alert</td>
    </tr>
  </tbody>
</table>

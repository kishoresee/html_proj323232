Here is the entire content you requested, formatted using HTML tables — ready for use in a .html file or a GitHub .md (if HTML is supported):

⸻

1. Installation & Deployment Instructions

Development Environment (Local - VS Code)

<table border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; width: 100%;">
  <thead style="background-color: #f2f2f2;">
    <tr><th>Step</th><th>Details</th></tr>
  </thead>
  <tbody>
    <tr><td>Code Editor</td><td>Install <strong>Visual Studio Code</strong></td></tr>
    <tr><td>File Structure</td><td>Create <code>.html</code> file with embedded HTML, JSOM, and Bootstrap</td></tr>
    <tr><td>Testing</td><td>Use <strong>Live Server</strong> extension in VS Code or open in browser for preview</td></tr>
  </tbody>
</table>



⸻

Deployment Environment (SharePoint Subsite)

<table border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; width: 100%;">
  <thead style="background-color: #f2f2f2;">
    <tr><th>Step</th><th>Details</th></tr>
  </thead>
  <tbody>
    <tr><td>SharePoint Access</td><td>Ensure you have <strong>edit rights</strong> to the subsite and Site Assets library</td></tr>
    <tr><td>Upload Code File</td><td>Upload your <code>.html</code> file to Site Assets or a document library</td></tr>
    <tr><td>Copy File URL</td><td>Right-click the uploaded file > <strong>Copy link</strong></td></tr>
    <tr><td>Embed in Page</td><td>Add a <strong>Content Editor Web Part</strong> to the page > Paste the link in “Content Link”</td></tr>
    <tr><td>Save & Publish</td><td>Your code will now run within the SharePoint page using JSOM</td></tr>
  </tbody>
</table>



⸻

2. Software Requirements

<table border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; width: 100%;">
  <thead style="background-color: #f2f2f2;">
    <tr><th>Component</th><th>Version/Requirement</th><th>Purpose</th></tr>
  </thead>
  <tbody>
    <tr><td>SharePoint</td><td>SharePoint 2013 / Online (Classic)</td><td>Platform for hosting solution</td></tr>
    <tr><td>Browser</td><td>Chrome / Edge / Firefox</td><td>Runs client-side JSOM scripts</td></tr>
    <tr><td>Visual Studio Code</td><td>Latest (Recommended)</td><td>Code writing and editing</td></tr>
    <tr><td>Bootstrap CDN</td><td>v4.5.2 or later</td><td>UI layout and responsive design</td></tr>
    <tr><td>jQuery CDN</td><td>v3.6.0 or later</td><td>DOM manipulation and JSOM compatibility</td></tr>
  </tbody>
</table>



⸻

3. Project Dependencies

<table border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; width: 100%;">
  <thead style="background-color: #f2f2f2;">
    <tr><th>Dependency</th><th>Type</th><th>Source / Link</th></tr>
  </thead>
  <tbody>
    <tr>
      <td>Bootstrap CSS</td>
      <td>Front-end UI</td>
      <td><code>&lt;link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css"&gt;</code></td>
    </tr>
    <tr>
      <td>Bootstrap JS</td>
      <td>Front-end JS</td>
      <td><code>&lt;script src="https://cdn.jsdelivr.net/npm/bootstrap@4.5.2/dist/js/bootstrap.bundle.min.js"&gt;&lt;/script&gt;</code></td>
    </tr>
    <tr>
      <td>Font Awesome (optional)</td>
      <td>Icons</td>
      <td><code>&lt;link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css"&gt;</code></td>
    </tr>
    <tr>
      <td>jQuery</td>
      <td>JavaScript</td>
      <td><code>&lt;script src="https://code.jquery.com/jquery-3.6.0.min.js"&gt;&lt;/script&gt;</code></td>
    </tr>
    <tr>
      <td>JSOM (SharePoint native)</td>
      <td>Script</td>
      <td>Available by default in SharePoint Classic pages</td>
    </tr>
    <tr>
      <td>Content Editor Web Part</td>
      <td>Web Part</td>
      <td>Used to embed custom HTML in SharePoint pages</td>
    </tr>
  </tbody>
</table>



⸻

Would you like me to export this into a single .html file for download or testing?

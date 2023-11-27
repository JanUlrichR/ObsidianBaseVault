<%* 
const project = await tp.system.prompt("Project name", "");

const filename = "🛠️ Projects/" + project.replace(/[^a-z0-9]/gi, '-').toLowerCase();

setTimeout(() => {
  app.fileManager.processFrontMatter(tp.config.target_file, frontmatter => {
  frontmatter["name"] = project;
  })
}, 200)
setTimeout(() => {
  tp.file.move(filename);
}, 400)
-%>
# Project - <% project %>

<% tp.file.cursor(0) %>


# Tasks
## Todo
```dataview
TABLE status AS Status
FROM "✅ Tasks"
WHERE project = this.file.frontmatter.name and status != "Closed"
SORT status DESC
```
## Closed
```dataview
TABLE status AS Status
FROM "✅ Tasks"
WHERE project = this.file.frontmatter.name and status = "Closed"
SORT status DESC
```
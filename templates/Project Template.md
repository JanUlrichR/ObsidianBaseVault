<%-*
	const project = await tp.system.prompt("Project name", "");
%>
---
name:  <% project %>
---
<% tp.file.move("🛠️ Projects/" + project ) %>
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
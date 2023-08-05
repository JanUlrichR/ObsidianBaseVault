<%-*
	const idea = await tp.system.prompt("Idea Summary", "");
%>
---
name:  <% idea %>
origin: <% tp.system.prompt("Inspiration", "None") %>
---
<% tp.file.move("💡 Ideas/" + idea ) %>
# Idea - <% idea %>

<% tp.file.cursor(1) %>


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
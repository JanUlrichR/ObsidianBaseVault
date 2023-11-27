<%* 
const idea = await tp.system.prompt("Idea Summary", "");
const inspiration = await tp.system.prompt("Inspiration", "None");

const filename = "💡 Ideas/" + idea.replace(/[^a-z0-9]/gi, '-').toLowerCase();

setTimeout(() => {
  app.fileManager.processFrontMatter(tp.config.target_file, frontmatter => {
  frontmatter["name"] = idea;
  frontmatter["origin"] = inspiration;
  })
}, 200)
setTimeout(() => {
  tp.file.move(filename );
}, 400)
-%>
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
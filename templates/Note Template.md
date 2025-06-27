---
date_created: Friday, June 27th 2025, 2:16:45 pm
date_modified: Friday, June 27th 2025, 2:17:51 pm
---
<%* 
const note = await tp.system.prompt("Note Topic", "");

const filename = "📝Notes/" + note.replace(/[^a-z0-9]/gi, '-').toLowerCase();

setTimeout(() => {
  app.fileManager.processFrontMatter(tp.config.target_file, frontmatter => {
  frontmatter["name"] = note;
  })
}, 200)
setTimeout(() => {
  tp.file.move(filename );
}, 400)
-%>
# Note - <% note %>

<% tp.file.cursor(1) %>

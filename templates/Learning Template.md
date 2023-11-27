<%* 
const learning = await tp.system.prompt("Learning Topic", "");
const reason = await tp.system.prompt("Reason", "None");

const filename = "🧠 Learning/" + learning;

setTimeout(() => {
  app.fileManager.processFrontMatter(tp.config.target_file, frontmatter => {
  frontmatter["name"] = learning;
  frontmatter["origin"] = reason;
  })
}, 200)
setTimeout(() => {
  tp.file.move(filename );
}, 400)
-%>
# Learning - <% learning %>

<% tp.file.cursor(1) %>

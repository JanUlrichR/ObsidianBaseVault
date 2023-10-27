<%* 
const project = await tp.system.prompt("Project", "");
const summary = await tp.system.prompt("Summary", "");
const taskKey = project + "-" + summary;
const origin = await tp.system.prompt("Origin", "");
const priority =  tp.system.suggester(["🟩","🟨","🟥"], ["🟩","🟨","🟥"])

const filename = "✅ Tasks/" + taskKey

setTimeout(() => {
  app.fileManager.processFrontMatter(tp.config.target_file, frontmatter => {
  frontmatter["name"] = taskKey;
  frontmatter["origin"] = origin;
  frontmatter["category"] = "Inbox";
  frontmatter["status"] = "Open";
  frontmatter["project"] = project;
  frontmatter["priority"] = priority;
  frontmatter["archived"] = false;
  })
}, 200)
setTimeout(() => {
  tp.file.move("✅ Tasks/" + taskKey);
}, 400)
-%>
# [Origin](<% origin %>)

# Project task - <% summary %>

Task information here..

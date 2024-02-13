<%* 
const projectsPath = "🛠️ Projects"
const project = (await tp.system.suggester((item) => item.basename, this.app.vault.getMarkdownFiles().filter(file => file.path.substr(0, file.path.lastIndexOf("/")) == projectsPath))).basename;
const summary = await tp.system.prompt("Summary", "");
const origin = await tp.system.prompt("Origin", "");
const priority =  tp.system.suggester(["🟩","🟨","🟥"], ["🟩","🟨","🟥"])

const filename = "✅ Tasks/" +project.replace(/[^a-z0-9]/gi, '-')+"/"+ summary.replace(/[^a-z0-9]/gi, '-').toLowerCase()

setTimeout(() => {
  app.fileManager.processFrontMatter(tp.config.target_file, frontmatter => {
  frontmatter["name"] = summary;
  frontmatter["origin"] = origin;
  frontmatter["category"] = "Inbox";
  frontmatter["status"] = "Open";
  frontmatter["project"] = project;
  frontmatter["priority"] = priority;
  frontmatter["archived"] = false;
  })
}, 200)
setTimeout(() => {
  tp.file.move(filename);
}, 400)
-%>
# [Origin](<% origin %>)

# Project task - <% summary %>

Task information here..

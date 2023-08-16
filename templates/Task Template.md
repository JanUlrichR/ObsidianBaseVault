<%-*
	const project = await tp.system.prompt("Project", "");
	const summary = await tp.system.prompt("Summary", "");
	const taskKey = project + "-" + summary;
	const origin = await tp.system.prompt("Origin", "");
%>
---
name:  <% taskKey %>
origin: 
category: Inbox
status: Open
project: <% project %>
complexity: <% tp.system.suggester(["🟩","🟨","🟥"], ["🟩","🟨","🟥"]) %>

dueDate:
workDates:
creationDate:  
updateDate:

openDate:
blockedDate:
delegatedDate:
inprogressDate:
doneDate:
---
<% tp.file.move("✅ Tasks/" + taskKey ) %>
# [Origin](<% origin %>) 
```dataviewjs
const {createButton} = app.plugins.plugins["buttons"]  
const {update} = app.plugins.plugins['metaedit'].api  
  
const changeStatus = async (file, value) => {  
    await update("status", value, file)  
}  
  
const statusButton = (status, page) => createButton({  
    app,  
    el: this.container,  
    args: {name: status},  
    clickOverride: {click: file => changeStatus(file, status), params: [page.file.path, 'date']}  
})  
  
  
dv.table(["Current", "Status", dv.current()['status']], [dv.current()].map(page => ["Open", "In Progress", "Blocked", "Delegated", "Closed"].map(status => statusButton(status, page))  ))
```
# Project task - <% summary %>

Task information here..


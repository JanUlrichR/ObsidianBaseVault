<%-*
	const project = await tp.system.prompt("Project", "");
	const summary = await tp.system.prompt("Summary", "");
	const taskKey = project + "-" + summary
%>
---
name:  <% taskKey %>
origin: <% tp.system.prompt("Origin", "") %>
category: Inbox
status: Open
project: <% project %>
complexity: <% tp.system.suggester(["🟩","🟨","🟥"], ["🟩","🟨","🟥"]) %>

dueDate:
workDates:
creationDate: [[ dailys/2023-08-04 ]]
updateDate: 2023-08-04 21:37

openDate:
blockedDate:
delegatedDate:
inprogressDate:
doneDate:
---
<% tp.file.move("✅ Tasks/" + taskKey ) %>
# Project task - <% summary %>

Task information here..


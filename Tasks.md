---
obsidianUIMode: preview
---
# In Progress
```dataviewjs
const {createButton} = app.plugins.plugins["buttons"]
const {update} = app.plugins.plugins['metaedit'].api

const changeStatus = async (file, value) => {
    await update("status", value, file)
}

dv.table(["Task", "Comp", "","",""], dv.pages('"✅ Tasks"')
	.filter(t => t.status === "In Progress")
	.filter(t => t.category !== "Inbox")
	.map(t => [
		t.file.link,
		t['complexity'],
		createButton({app, el: this.container, args: {name: "Delegate"}, clickOverride: {click: file => changeStatus(file,"Delegated"), params: [t.file.path, 'date']}}),
		createButton({app, el: this.container, args: {name: "Blocked"}, clickOverride: {click: file => changeStatus(file,"Blocked"), params: [t.file.path, 'date']}}),
		createButton({app, el: this.container, args: {name: "Close"}, clickOverride: {click: file => changeStatus(file,"Closed"), params: [t.file.path, 'date']}}),
		])
)
```
# Blocked
```dataviewjs
const {createButton} = app.plugins.plugins["buttons"]
const {update} = app.plugins.plugins['metaedit'].api

const changeStatus = async (file, value) => {
    await update("status", value, file)
}

dv.table(["Task", "Complexity", "","",""], dv.pages('"✅ Tasks"')
	.filter(t => t.status === "Blocked")
	.filter(t => t.category !== "Inbox")
	.map(t => [
		t.file.link,
		t['complexity'],
		createButton({app, el: this.container, args: {name: "Continue"}, clickOverride: {click: file => changeStatus(file,"Open"), params: [t.file.path, 'date']}}),
		"",""
		])
)
```
# Delegated
```dataviewjs
const {createButton} = app.plugins.plugins["buttons"]
const {update} = app.plugins.plugins['metaedit'].api

const changeStatus = async (file, value) => {
    await update("status", value, file)
}

dv.table(["Task", "Complexity", "",""], dv.pages('"✅ Tasks"')
	.filter(t => t.status === "Delegated")
	.filter(t => t.category !== "Inbox")
	.map(t => [
		t.file.link,
		t['complexity'],
		createButton({app, el: this.container, args: {name: "Retake"}, clickOverride: {click: file => changeStatus(file,"Open"), params: [t.file.path, 'date']}}),
		createButton({app, el: this.container, args: {name: "Close"}, clickOverride: {click: file => changeStatus(file,"Closed"), params: [t.file.path, 'date']}}),
		])
)
```
# Open
```dataviewjs
const {createButton} = app.plugins.plugins["buttons"]
const {update} = app.plugins.plugins['metaedit'].api

const changeStatus = async (file, value) => {
    await update("status", value, file)
}

dv.table(["Task", "Complexity", "",""], dv.pages('"✅ Tasks"')
	.filter(t => t.status === "Open")
	.filter(t => t.category !== "Inbox")
	.map(t => [
		t.file.link,
		t['complexity'],
		createButton({app, el: this.container, args: {name: "Start Progress"}, clickOverride: {click: file => changeStatus(file,"In Progress"), params: [t.file.path, 'date']}}),
		])
)
```
# Done
```dataviewjs
const {createButton} = app.plugins.plugins["buttons"]
const {update} = app.plugins.plugins['metaedit'].api

const changeStatus = async (file, value) => {
    await update("status", value, file)
}

dv.table(["Task", "Complexity", "",""], dv.pages('"✅ Tasks"')
	.filter(t => t.status === "Closed")
	.filter(t => t.category !== "Inbox")
	.map(t => [
		t.file.link,
		t['complexity'],
		createButton({app, el: this.container, args: {name: "Reopen"}, clickOverride: {click: file => changeStatus(file,"Open"), params: [t.file.path, 'date']}}),
		])
)
```
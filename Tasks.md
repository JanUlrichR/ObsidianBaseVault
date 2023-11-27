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

dv.table(["Task", "Complexity", "Category"], dv.pages('"✅ Tasks"')
	.filter(t => t.status === "In Progress")
	.filter(t => t.category !== "Inbox")
	.map(t => [
		t.file.link,
		t['complexity'],
		t['category'],
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

dv.table(["Task", "Complexity", "Category"], dv.pages('"✅ Tasks"')
	.filter(t => t.status === "Blocked")
	.filter(t => t.category !== "Inbox")
	.map(t => [
		t.file.link,
		t['complexity'],
		t['category'],
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

dv.table(["Task", "Complexity", "Category"], dv.pages('"✅ Tasks"')
	.filter(t => t.status === "Delegated")
	.filter(t => t.category !== "Inbox")
	.map(t => [
		t.file.link,
		t['complexity'],
		t['category'],
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

dv.table(["Task", "Complexity", "Category"], dv.pages('"✅ Tasks"')
	.filter(t => t.status === "Open")
	.filter(t => t.category !== "Inbox")
	.map(t => [
		t.file.link,
		t['complexity'],
		t['category'],
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

dv.table(["Task", "Complexity", "Category"], dv.pages('"✅ Tasks"')
	.filter(t => t.status === "Closed")
	.filter(t => t.category !== "Inbox")
	.map(t => [
		t.file.link,
		t['complexity'],
		t['category'],
		])
)
```

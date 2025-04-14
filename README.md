# Vue.js ToDo List

A simple and stylish ToDo List application built with Vue.js. You can create, search, filter, edit, delete, and mark tasks as completed. Tasks are stored in `localStorage`, and you can sort them by status.

## 🚀 Features

- ✅ Add new tasks with deadlines
- 🔍 Real-time search filter
- 🔁 Sort tasks:
  - All
  - Completed
  - In progress
- ⛔ Prevent adding past dates
- ⏰ Highlight overdue tasks in red
- ✏️ Edit and update tasks
- 🗑️ Delete tasks
- 💾 Tasks saved to `localStorage`
- 🌐 Deployable via GitHub Pages

## 🧱 Project Structure

```
├── public/
├── src/
│   ├── components/
│   │   ├── TaskForm.vue
│   │   ├── TaskList.vue
│   │   └── TaskItem.vue
│   ├── App.vue
│   └── main.js
├── vue.config.js
└── README.md
```

## 📆 Installation

```bash
git clone https://github.com/vetam2008/Vue.js-ToDoList.git
cd Vue.js-ToDoList
npm install
npm run serve
```

## 🚀 Deploy to GitHub Pages

Make sure you have `gh-pages` installed:

```bash
npm install gh-pages --save-dev
```

In `package.json`, add:

```json
"homepage": "https://vetam2008.github.io/Vue.js-ToDoList",
"scripts": {
  "build": "vue-cli-service build",
  "deploy": "gh-pages -d dist"
}
```

In `vue.config.js`:

```js
module.exports = {
  publicPath: '/Vue.js-ToDoList/'
};
```

Then run:

```bash
npm run build
npm run deploy
```

Your app will be live at:  
👉 [https://vetam2008.github.io/Vue.js-ToDoList](https://vetam2008.github.io/Vue.js-ToDoList)

## 📸 Screenshots

> _(Add screenshots if you'd like, for better presentation)_

## 📄 License

MIT — Feel free to use, modify, and share!


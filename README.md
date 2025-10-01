<!-- index.html -->
<!DOCTYPE html>
<html lang="fa">
<head>
  <meta charset="UTF-8">
  <title>📝 لیست کارها (نسخه ذخیره‌دار)</title>
  <style>
    body {
      font-family: sans-serif;
      text-align: center;
      background: linear-gradient(135deg, #d4fc79, #96e6a1);
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
    }
    h1 {
      margin-bottom: 20px;
    }
    #taskInput {
      padding: 10px;
      border-radius: 8px;
      border: 1px solid #ccc;
      width: 250px;
      font-size: 16px;
    }
    button {
      padding: 10px 15px;
      margin-left: 10px;
      border: none;
      border-radius: 8px;
      background: #333;
      color: white;
      cursor: pointer;
      transition: 0.3s;
    }
    button:hover {
      background: #555;
    }
    ul {
      list-style: none;
      padding: 0;
      margin-top: 20px;
      width: 300px;
    }
    li {
      background: #fff;
      margin: 5px 0;
      padding: 10px;
      border-radius: 8px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      box-shadow: 0 2px 6px rgba(0,0,0,0.1);
    }
    .done {
      text-decoration: line-through;
      color: gray;
    }
  </style>
</head>
<body>
  <h1>📝 لیست کارها (با ذخیره‌سازی)</h1>
  <input id="taskInput" type="text" placeholder="کار جدید...">
  <button onclick="addTask()">➕ افزودن</button>
  <ul id="taskList"></ul>

  <script>
    let tasks = JSON.parse(localStorage.getItem("tasks")) || [];

    function renderTasks() {
      const taskList = document.getElementById("taskList");
      taskList.innerHTML = "";
      tasks.forEach((task, index) => {
        const li = document.createElement("li");
        li.innerHTML = `
          <span onclick="toggleTask(${index})" class="${task.done ? 'done' : ''}">
            ${task.text}
          </span>
          <button onclick="removeTask(${index})">🗑️</button>
        `;
        taskList.appendChild(li);
      });
      localStorage.setItem("tasks", JSON.stringify(tasks));
    }

    function addTask() {
      const input = document.getElementById("taskInput");
      const taskText = input.value.trim();
      if (taskText === "") return;
      tasks.push({ tex

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Neon Task Manager</title>
  <style>
    body {
      background-color: #0f0f0f;
      color: #00ffe0;
      font-family: 'Segoe UI', sans-serif;
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 2em;
    }

    h1 {
      font-size: 2.5em;
      margin-bottom: 0.5em;
      text-shadow: 0 0 10px #00ffe0;
    }

    .task-input {
      display: flex;
      gap: 1em;
      margin-bottom: 2em;
    }

    input[type="text"], input[type="date"] {
      padding: 0.5em;
      border: none;
      border-radius: 5px;
      background-color: #1a1a1a;
      color: #00ffe0;
    }

    button {
      padding: 0.5em 1em;
      background-color: #00ffe0;
      color: #0f0f0f;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      font-weight: bold;
    }

    ul {
      list-style: none;
      padding: 0;
      width: 100%;
      max-width: 600px;
    }

    li {
      background-color: #1a1a1a;
      margin-bottom: 1em;
      padding: 1em;
      border-radius: 8px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      box-shadow: 0 0 10px #00ffe0;
    }

    .completed {
      text-decoration: line-through;
      opacity: 0.6;
    }

    .task-info {
      flex-grow: 1;
    }

    .task-actions button {
      margin-left: 0.5em;
    }
  </style>
</head>
<body>

  <h1>📝 Neon Task Manager</h1>

  <div class="task-input">
    <input type="text" id="taskText" placeholder="Enter a task">
    <input type="date" id="taskDate">
    <button onclick="addTask()">Add Task</button>
  </div>

  <ul id="taskList"></ul>

  <script>
    function addTask() {
      const text = document.getElementById('taskText').value.trim();
      const date = document.getElementById('taskDate').value;
      if (!text) return;

      const li = document.createElement('li');
      const info = document.createElement('div');
      info.className = 'task-info';
      info.innerHTML = `<strong>${text}</strong><br><small>Due: ${date || 'No date'}</small>`;

      const actions = document.createElement('div');
      actions.className = 'task-actions';

      const completeBtn = document.createElement('button');
      completeBtn.textContent = '✅';
      completeBtn.onclick = () => {
        info.classList.toggle('completed');
      };

      const deleteBtn = document.createElement('button');
      deleteBtn.textContent = '🗑️';
      deleteBtn.onclick = () => {
        li.remove();
      };

      actions.appendChild(completeBtn);
      actions.appendChild(deleteBtn);

      li.appendChild(info);
      li.appendChild(actions);

      document.getElementById('taskList').appendChild(li);
      document.getElementById('taskText').value = '';
      document.getElementById('taskDate').value = '';
    }
  </script>

</body>
</html>

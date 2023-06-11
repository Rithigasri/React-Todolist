# EXPERIMENT 05:DEVELOP A TO DO LIST USING REACT FRAMEWORK
## AIM:
To develop a to-do list using react framework.
## ALGORITHM:
1. Cretae a new react project named todolist.
2. Import required hooks from the react.
3. Program the function App() with required components.
4. Export the default app at the endd of function component.
5. Add required styling to the component.
6. Display the project using the command npm start.
## PROGRAM:
```
DEVELOPED BY: RITHIGA SRI.B
REGISTER NUMBER:212221230083
```
### App.js:
```
import React, { useState } from 'react';
import './App.css';

function App() {
  const [tasks, setTasks] = useState([]);
  const [newTask, setNewTask] = useState('');
  const [editTaskId, setEditTaskId] = useState(null);

  const handleAddTask = () => {
    if (newTask.trim() !== '') {
      const newTaskItem = {
        id: Date.now(),
        text: newTask,
        completed: false,
      };
      setTasks([...tasks, newTaskItem]);
      setNewTask('');
    }
  };

  const handleEditTask = (id, newText) => {
    const updatedTasks = tasks.map((task) => {
      if (task.id === id) {
        return {
          ...task,
          text: newText,
        };
      }
      return task;
    });
    setTasks(updatedTasks);
    setEditTaskId(null);
  };

  const handleDeleteTask = (id) => {
    const updatedTasks = tasks.filter((task) => task.id !== id);
    setTasks(updatedTasks);
  };

  const handleToggleComplete = (id) => {
    const updatedTasks = tasks.map((task) => {
      if (task.id === id) {
        return {
          ...task,
          completed: !task.completed,
        };
      }
      return task;
    });
    setTasks(updatedTasks);
  };

  return (
    <div className="todo-app">
      <h1 style={{textAlign:"center"}}>TO-DO LIST</h1>
      <div className="task-input">
        <input
          type="text"
          value={newTask}
          onChange={(e) => setNewTask(e.target.value)}
          placeholder="Enter a new task"
        />
        <button onClick={handleAddTask}>Add</button>
      </div>
      <ul className="task-list">
        {tasks.map((task) => (
          <li key={task.id} className={task.completed ? 'completed' : ''}>
            <input
              type="checkbox"
              checked={task.completed}
              onChange={() => handleToggleComplete(task.id)}
            />
            {editTaskId === task.id ? (
              <input
                type="text"
                value={task.text}
                onChange={(e) => handleEditTask(task.id, e.target.value)}
              />
            ) : (
              <span>{task.text}</span>
            )}
            <div className="task-actions">
              {editTaskId === task.id ? (
                <button onClick={() => handleEditTask(task.id, task.text)}>Save</button>
              ) : (
                <button onClick={() => setEditTaskId(task.id)}>Edit</button>
              )}
              <button onClick={() => handleDeleteTask(task.id)}>Delete</button>
            </div>
          </li>
        ))}
      </ul>
    </div>
  );
}
export default App;
```
### App.css
```
.todo-app {
  width: 400px;
  margin: 50px auto;
  background-color:lightgreen;
  padding:20px;
}

.task-input {
  display: flex;
  margin-bottom: 10px;
}

.task-input input[type='text'] {
  flex-grow: 1;
  height: 30px;
  font-size: 16px;
  padding: 5px;
}

.task-input button {
  height: 30px;
  margin-left: 10px;
  background-color: #4caf50;
  color: #fff;
  border: none;
  cursor: pointer;
}

.task-list {
  list-style: none;
  padding: 0;
}

.task-list li {
  display: flex;
  align-items: center;
  padding: 10px;
  background-color: #f1f1f1;
  margin-bottom: 5px;
  text-decoration: none;
}

.task-list li.completed span {
  text-decoration: line-through;
}

.task-list li input[type='checkbox'] {
  margin-right: 10px;
}

.task-list li input[type='text'] {
  flex-grow: 1;
  height: 25px;
  font-size: 14px;
  padding: 3px;
}

.task-list li button {
  margin-left: 10px;
  background-color: #ff4d4d;
  color: #fff;
  border: none;
  cursor: pointer;
}
.task-actions {
  display: flex;
}

.task-actions button {
  margin-left: 5px;
}

```
## OUTPUT:
![image](https://github.com/Rithigasri/React-Todolist/assets/93427256/cc12eedf-1c2a-4024-b5c6-83fc86dfb0d4)
![image](https://github.com/Rithigasri/React-Todolist/assets/93427256/ba8769f8-3022-4dde-8edb-a1d51de4484c)

## RESULT:
Thus, a to-do list using react framework is developed succesfully.

<template>
  <div>
    <h1>Task List</h1>
<div class="task-input">
  <input type="text" placeholder="Add a new task" v-model="newTask" @keyup.enter="addTask">
  <button @click="addTask">Add</button>
</div>

<div class="filters">
  <span :class="{ 'active': filter == 'all' }" @click="setFilter('all')">All</span>
  <span :class="{ 'active': filter == 'pending' }" @click="setFilter('pending')">Pending</span>
  <span :class="{ 'active': filter == 'completed' }" @click="setFilter('completed')">Completed</span>
</div>

<ul>
  <li v-for="task in filteredTasks" :key="task.id">
    <input type="checkbox" v-model="task.completed" @change="updateTask(task)">
    <span :class="{ 'completed': task.completed }">{{ task.text }}</span>
    <button @click="deleteTask(task)">Delete</button>
  </li>
</ul>
  </div>
</template>
<script>
export default {
  name: 'TaskList',
  data() {
    return {
      newTask: '',
      tasks: [
    
      ],
      filter: 'all',
    };
  },
  computed: {
    filteredTasks() {
      if (this.filter === 'all') {
        return this.tasks;
      } else if (this.filter === 'pending') {
        return this.tasks.filter((task) => !task.completed);
      } else if (this.filter === 'completed') {
        return this.tasks.filter((task) => task.completed);
      }
    },
  },
  methods: {
    addTask() {
      if (!this.newTask) return;

      const newTask = {
        id: Math.max(...this.tasks.map((task) => task.id)) + 1,
        text: this.newTask,
        completed: false,
      };

      this.tasks.push(newTask);
      this.newTask = '';
    },
    updateTask(task) {
      task.completed = !task.completed;
    },
    deleteTask(task) {
      const index = this.tasks.indexOf(task);
      this.tasks.splice(index, 1);
    },
    setFilter(filter) {
      this.filter = filter;
    },
  },
};
</script>
<style>
.completed {
  text-decoration: line-through;
}
.filters {
  margin: 1rem 0;
}
.filters span {
  margin-right: 1rem;
  cursor: pointer;
}
.filters span.active {
  font-weight: bold;
}
.task-input {
  display: flex;
  margin-bottom: 1rem;
}
.task-input input {
  flex-grow: 1;
  margin-right: 1rem;
  padding: 0.5rem;
  font-size: 1.2rem;
}
.task-input button {
  background-color: #4CAF50;
  color: white;
  padding: 0.5rem;
  border: none;
  border-radius: 0.25rem;
  cursor: pointer;
  font-size: 1.2rem;
}
.task-input button:hover {
  background-color: #3e8e41;
}
li {
  margin-bottom: 0.5rem;
  display: flex;
  align-items: center;
}
li {
margin-bottom: 0.5rem;
display: flex;
align-items: center;
}
li input[type="checkbox"] {
margin-right: 0.5rem;
}
li button {
background-color: #f44336;
color: white;
padding: 0.5rem;
border: none;
border-radius: 0.25rem;
cursor: pointer;
font-size: 1.2rem;
margin-left: auto;
}
li button:hover {
background-color: #e53935;
}
</style>
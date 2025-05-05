<template>
  <main>
    <h1>Daftar Kegiatan</h1>
    <form @submit.prevent="addTask">
      <input v-model="newTask" placeholder="Tambah kegiatan..." />
      <button type="submit">Tambah</button>
    </form>

    <label>
      <input type="checkbox" v-model="showOnlyUnfinished" />
      Tampilkan hanya yang belum selesai
    </label>

    <ul>
      <li v-for="(task, index) in filteredTasks" :key="index">
        <span :class="{ done: task.done }">{{ task.text }}</span>
        <input type="checkbox" v-model="task.done" />
        <button @click="removeTask(index)">Hapus</button>
      </li>
    </ul>
  </main>
</template>

<script>
export default {
  data() {
    return {
      newTask: '',
      tasks: [
      { text: 'Belajar VueJS', done: false },
      { text: 'Makan Siang', done: false }
    ],
    showOnlyUnfinished: false
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim()) {
        this.tasks.push({ text: this.newTask, done: false });
        this.newTask = '';
      }
    },
    removeTask(index) {
      this.tasks.splice(index, 1);
    }
  },
  computed: {
  filteredTasks() {
    if (this.showOnlyUnfinished) {
      return this.tasks.filter(task => !task.done);
    }
    return this.tasks;
  }
}
};
</script>
<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  background-color: #0f1115;
  color: #ffffff;
  font-family: 'Inter', sans-serif;
}

main {
  max-width: 480px;
  margin: 40px auto;
  padding: 20px;
  background-color: #1a1d24;
  border-radius: 18px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
}

h1 {
  font-size: 26px;
  font-weight: 600;
  margin-bottom: 24px;
  color: #ffffff;
}

form {
  display: flex;
  margin-bottom: 20px;
  gap: 10px;
}

input[type="text"] {
  flex: 1;
  padding: 12px 16px;
  background-color: #2a2d34;
  border: none;
  border-radius: 30px;
  color: #ffffff;
  font-size: 14px;
  outline: none;
  transition: background 0.2s;
}

input[type="text"]::placeholder {
  color: #777;
}

button {
  padding: 12px 18px;
  border: none;
  border-radius: 30px;
  background-color: #2563eb;
  color: #fff;
  font-weight: 600;
  cursor: pointer;
  transition: background-color 0.3s;
}

button:hover {
  background-color: #1e4ecf;
}

label {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 14px;
  margin-bottom: 14px;
  color: #bbb;
}

ul {
  list-style: none;
}

li {
  display: flex;
  align-items: center;
  padding: 14px 10px;
  margin-bottom: 12px;
  border-radius: 12px;
  background-color: #2a2d34;
  transition: background 0.2s ease-in-out;
}

li:hover {
  background-color: #32363e;
}

/* ✅ Custom Circular Checkbox with Filled Dot */
input[type="checkbox"] {
  appearance: none;
  -webkit-appearance: none;
  width: 20px;
  height: 20px;
  border: 2px solid #2563eb;
  border-radius: 50%;
  position: relative;
  margin-right: 12px;
  background-color: transparent;
  cursor: pointer;
  transition: all 0.2s ease;
}

input[type="checkbox"]:checked::before {
  content: "";
  position: absolute;
  top: 3px;
  left: 3px;
  width: 10px;
  height: 10px;
  background-color: #2563eb;
  border-radius: 50%;
}

span {
  flex: 1;
  font-size: 15px;
  color: #ffffff;
}

.done {
  text-decoration: line-through;
  color: #777;
}
</style>
<template>
  <main>
    <h1>Daftar Kegiatan</h1>
    <form @submit.prevent="addTask">
      <input v-model="newTask" placeholder="Tambah kegiatan..." />
      <button type="submit">Tambah</button>
    </form>

    <ul>
      <li v-for="(task, index) in tasks" :key="index">
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
    ]
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim()) {
        this.tasks.push(this.newTask);
        this.newTask = '';
      }
    },
    removeTask(index) {
      this.tasks.splice(index, 1);
    }
  }
};
</script>

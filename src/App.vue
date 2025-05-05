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
.done {
  text-decoration: line-through;
  color: gray;
}
</style>

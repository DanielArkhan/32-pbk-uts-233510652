<template>
  <main>
    <h1>Daftar Kegiatan</h1>
    <form @submit.prevent="addTask">
      <input v-model="newTask" placeholder="Tambah kegiatan..." />
      <button type="submit">Tambah</button>
    </form>

    <ul>
      <li v-for="(task, index) in tasks" :key="index">
        {{ task }}
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
      tasks: ['Belajar VueJS', 'Makan Siang']
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

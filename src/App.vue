<template>
  <main>
    <h1>Daftar Kegiatan</h1>
    <ul>
      <li v-for="(task, index) in tasks" :key="index">
        {{ task }}
      </li>
    </ul>
  </main>
</template>

<script>
export default {
  data() {
    return {
      tasks: ['Belajar VueJS', 'Makan Siang']
    };
  }
};
</script>

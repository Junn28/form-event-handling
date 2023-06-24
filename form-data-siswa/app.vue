<script setup>
import Form from "./components/form.vue";
import DaftarSiswa from "./components/daftar-siswa.vue";

const daftarSiswa = ref(null);
const getDataSiswa = onMounted((datas) => {
  daftarSiswa.value = datas;
  return daftarSiswa;
});
</script>

<template>
  <div class="p-2">
    <Form @parse-data-siswa="getDataSiswa" />
    <DaftarSiswa :data-siswa="daftarSiswa" />
  </div>
</template>

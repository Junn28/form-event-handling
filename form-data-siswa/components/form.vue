<script setup>
import "bootstrap/dist/css/bootstrap.css";
import "bootstrap-vue/dist/bootstrap-vue.css";

const form = reactive({
  daftar_siswa: [],
  no_induk_siswa: "",
  nama_siswa: "",
  nilai_tugas: "",
});

const emit = defineEmits(["parseDataSiswa"]);

const addDataSiswa = () => {
  const dataSiswa = {
    indukSiswa: form.no_induk_siswa,
    namaSiswa: form.nama_siswa,
    nilaiTugas: form.nilai_tugas,
  };
  form.daftar_siswa.push(dataSiswa);
  emit("parseDataSiswa", form.daftar_siswa);
};
</script>

<template>
  <div class="container p-2 bg-body-tertiary rounded-2 shadow">
    <form @submit.prevent="addDataSiswa">
      <div class="form-group row mb-2">
        <label for="no-induk-siswa" class="col-sm-4 col-form-label"
          >No Induk Siswa</label
        >
        <div class="col-sm-8">
          <input
            type="number"
            class="form-control"
            id="no-induk-siswa"
            placeholder="Masukkan No Induk Siswa"
            v-model="form.no_induk_siswa"
          />
        </div>
      </div>

      <div class="form-group row mb-2">
        <label for="nama-siswa" class="col-sm-4 col-form-label"
          >Nama Siswa</label
        >
        <div class="col-sm-8">
          <input
            type="text"
            class="form-control"
            id="nama-siswa"
            placeholder="Masukkan Nama Siswa"
            v-model="form.nama_siswa"
          />
        </div>
      </div>

      <div class="form-group row mb-3">
        <label for="nilai-tugas" class="col-sm-4 col-form-label"
          >Nilai Tugas</label
        >
        <div class="col-sm-8">
          <input
            type="number"
            class="form-control"
            id="nilai-tugas"
            placeholder="Masukkan Nilai Tugas"
            v-model="form.nilai_tugas"
          />
        </div>
      </div>

      <button type="submit" class="btn btn-primary me-2">Submit</button>
      <button type="button" class="btn btn-danger">Cancel</button>
    </form>
  </div>
</template>

<style scoped>
input::placeholder {
  opacity: 0.5;
  font-size: 12px;
  font-style: italic;
}
</style>

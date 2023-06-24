<script setup>
const props = defineProps(["dataSiswa"]);
const avgValue = computed(() => {
  const value = props.dataSiswa
    .map((data) => data.nilaiTugas)
    .reduce((value1, value2) => value1 + value2);

  return Math.floor(value / props.dataSiswa.length);
});
</script>

<template>
  <div class="container mt-4">
    <h1 class="text-center">Daftar Siswa</h1>
    <h3 v-if="!props.dataSiswa" class="text-center">Tidak ada data siswa</h3>
    <template v-else>
      <h3>Jumlah siswa: {{ props.dataSiswa.length }}</h3>
      <h3>Nilai rata-rata Siswa: {{ avgValue }}</h3>
      <div class="row row-cols-1 row-cols-lg-3 row-cols-md-2 p-2">
        <div
          v-for="(data, i) in props.dataSiswa"
          :key="i"
          class="border border-dark d-flex rounded-2 p-2"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="100"
            fill="currentColor"
            class="bi bi-person-square me-2"
            viewBox="0 0 16 16"
          >
            <path d="M11 6a3 3 0 1 1-6 0 3 3 0 0 1 6 0z" />
            <path
              d="M2 0a2 2 0 0 0-2 2v12a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V2a2 2 0 0 0-2-2H2zm12 1a1 1 0 0 1 1 1v12a1 1 0 0 1-1 1v-1c0-1-1-4-6-4s-6 3-6 4v1a1 1 0 0 1-1-1V2a1 1 0 0 1 1-1h12z"
            />
          </svg>
          <div>
            <p class="m-0">
              No. Induk:
              <span class="fw-semibold text-capitalize">{{
                data.indukSiswa
              }}</span>
            </p>
            <p class="m-0">
              Nama:
              <span class="fw-semibold text-capitalize">{{
                data.namaSiswa
              }}</span>
            </p>
            <p class="m-0">
              Nilai Tugas:
              <span class="fw-semibold text-capitalize">{{
                data.nilaiTugas
              }}</span>
            </p>
          </div>
        </div>
      </div>
    </template>
  </div>
</template>

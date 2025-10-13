<script setup>
import { ref } from 'vue'

defineProps({
  msg: String,
})

const count = ref(0)
</script>

<template>
  <h1>{{ msg }}</h1>

  <div class="card">
    <button type="button" @click="count++">hitungan adalah {{ count }}</button>
    <p>
      Ubah
      <code>components/HelloWorld.vue</code> untuk menguji HMR
    </p>
  </div>

  <p>
    Lihat
    <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank"
      >create-vue</a
    >, starter resmi Vue + Vite
  </p>
  <p>
    Pelajari lebih lanjut tentang Dukungan IDE untuk Vue di
    <a
      href="https://vuejs.org/guide/scaling-up/tooling.html#ide-support"
      target="_blank"
      >Panduan Peningkatan Skala Dokumentasi Vue</a
    >.
  </p>
  <p class="read-the-docs">Klik pada logo Vite dan Vue untuk mempelajari lebih lanjut</p>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>

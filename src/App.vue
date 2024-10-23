<template>
  <div id="app">
    <h1>Ваш IP-адрес:</h1>
    <p>{{ userIP }}</p>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const userIP = ref('Завантаження...');

onMounted(() => {
  fetch('https://api64.ipify.org?format=json')
    .then(response => response.json())
    .then(data => {
      userIP.value = data.ip;
    })
    .catch(() => {
      userIP.value = 'Не вдалося отримати IP';
    });
});
</script>

<style>

</style>
<script setup>
  const counter = useCounter();
  const { $hello } = useNuxtApp()
  const dataNew = ref('')
  const clickApi = async() => {
   const { data } = await useAsyncData('count', () => $fetch('/api/testApi'))
   dataNew.value = data.value.api;
  }
</script>
<template>
  <div>
  <h1>{{  dataNew }} {{  $hello('Trung') }}</h1>
  <button @click="clickApi">Click</button>
  <div>
    Counter: {{ counter }}
    <button @click="counter++">
      +
    </button>
    <button @click="counter--">
      -
    </button>
  </div>
</div>
</template>
<style lang="scss" scoped>
  div {
    h1 {
      @apply text-red-500;
    }
  }
</style>
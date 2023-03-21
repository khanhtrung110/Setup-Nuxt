<script setup lang="ts">
  const counter = useCounter();
  const router = useRouter();
  const route = useRoute();

  const { $hello } = useNuxtApp()
  const dataNew = ref('')
  const clickApi = async() => {
   const { data } = await useAsyncData('count', () => $fetch('/api/testApi'))
   dataNew.value = data.value.api;
  }
  const a = ref(1)
  // console.log('aToRef',aToRef);
  const aToRef = toRefs(a);
  console.log('aToRef',aToRef);
  
  watch(()=>a,(val)=> {
    console.log('this',val);
  },{deep: true})
  const injectData = inject('foo','default value');
  // console.log(injectData,123);

  console.log(123,route.fullPath);
  
  
</script>
<template>
  <div>
  <h1>{{  dataNew }} {{  $hello('Trung') }}</h1>
  <p>{{ $hello('What Your Name')  }}</p>
  <!-- <button @click="">Click</button> -->
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
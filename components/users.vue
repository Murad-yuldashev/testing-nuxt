<template>
  <div>
    <pre>{{ user }}</pre>
  </div>
</template>

<script setup>
const props = defineProps({
  user: {
    type: Array
  }
})
console.log(props?.user);
</script>


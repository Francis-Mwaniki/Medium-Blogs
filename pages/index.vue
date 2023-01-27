<script setup lang="ts">
let q = ref('')
const { result, search } = useAlgoliaSearch('test_index')
onMounted(async () => {
  await search({ query: q.value })
})
</script>
<template>
    <input type="search" name="" class=" ring" v-model="q" id="">
  <div class=" bg-slate-800 ring-red-300 ring text-black">{{ result }}</div>
</template>
<template>
  <div>
    <!-- Larger animate loader for mounting with v-if=mounting -->
    <div v-if="loading" class="flex justify-center items-center fixed inset-0 mx-auto">
      <div class="animate-spin">
        <img src="@/assets/loading.gif" alt="Logo" class="object-cover h-32 w-32" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["loading"],
  data() {
    return {};
  },
};
</script>

<style scoped></style>

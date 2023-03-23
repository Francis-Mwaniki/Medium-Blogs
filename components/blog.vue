<template>
  <div class="mb-8">
    <!-- author -->
    <div class="flex items-center mb-2">
      <img :src="post.image" class="w-10 h-10 rounded-full mr-2" alt="avatar" />
      <span class="text-gray-600 text-sm">{{ post.author }}</span>
    </div>
    <div class="flex items-center mb-2">
      <span class="text-gray-600 text-sm">{{ post.date }}</span>
      <span class="mx-2 text-gray-400">•</span>
      <span class="text-gray-600 text-sm">{{ post.readTime }} min read</span>
    </div>
    <h2 class="text-2xl font-semibold mb-2 text-indigo-700">
      <a :href="`${post.slug}`">{{ post.title }}...</a>
    </h2>
    <p class="text-gray-600">{{ post.excerpt }}</p>
  </div>
</template>

<script>
export default {
  props: ["post"],
};
</script>

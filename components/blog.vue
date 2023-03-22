<template>
  <div class="mb-8">
    <img :src="post.image" class="mb-4 rounded-lg" />
    <div class="flex items-center mb-2">
      <span class="text-gray-600 text-sm">{{ post.date }}</span>
      <span class="mx-2 text-gray-400">•</span>
      <span class="text-gray-600 text-sm">{{ post.readTime }} min read</span>
    </div>
    <h2 class="text-2xl font-semibold mb-2">
      <nuxt-link :to="`/blog/${post.slug}`">{{ post.title }}</nuxt-link>
    </h2>
    <p class="text-gray-600">{{ post.excerpt }}</p>
  </div>
</template>

<script>
export default {
  props: ["post"],
};
</script>

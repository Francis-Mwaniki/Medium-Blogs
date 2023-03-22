<script setup lang="ts">
import Blog from "~~/components/blog.vue";

const posts = ref([]);
const fetchBlogPost = async () => {
  let post_url = "http://localhost:4000/tasks";
  try {
    let response = await fetch(post_url);
    if (response.ok) {
      let data = await response.json();
      posts.value = <any>{
        title: data.items[""],
        slug: data.slug,
        excerpt: data.excerpt,
        date: data.date,
        readTime: data.readTime,
        image: data.image,
      };
      console.log(data);
    } else {
      let data = await response.json();
      console.log(`Error occurred`);
    }
  } catch (error) {}
};
fetchBlogPost();
onMounted(async () => {});
</script>
<template>
  <div>
    <!-- results  with tailwindcss-->

    <div class="max-w-3xl mx-auto mt-8">
      <div v-for="post in posts" :key="post">
        <Blog :post="post" />
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import Blog from "~~/components/blog.vue";

const posts = ref([]);
const loading = ref(true);
type typeOfPosts = {
  title: string;
  author: string;
  slug: string;
  excerpt: string;
  date: string;
  image: string;
  readTime: string;
};
const cleanedPosts = ref<typeOfPosts[]>([]);
const fetchBlogPost = async () => {
  loading.value = true;
  let post_url = "http://localhost:4000/tasks";
  try {
    let response = await fetch(post_url);
    if (response.ok) {
      let data = await response.json();
      posts.value = data.result.robotTasks.items[0].capturedLists["Posts list"];
      cleanedPosts.value = posts.value.map((post) => {
        return {
          title: post["Title"],
          author: post["Author"],
          slug: post["Post link"],
          excerpt: post["Description"],
          date: post["Post Date"],
          image: post["Image URL"] || "https://via.placeholder.com/150",
          readTime: post["Time to read"],
        };
      });
      loading.value = false;
      console.log(cleanedPosts.value);
    } else {
      loading.value = false;
      let data = await response.json();
      console.log(`Error occurred while fetching data: ${data}`);
    }
  } catch (error) {}
};

onMounted(async () => {
  setTimeout(() => {
    loading.value = false;
  }, 3000);
  await fetchBlogPost();
});
</script>
<template>
  <div>
    <!-- results  with tailwindcss-->

    <div class="max-w-3xl mx-auto mt-8">
      <Loader :loading="loading" />
      <h1 class="text-4xl font-semibold mb-8 text-center">Blog</h1>

      <div v-for="post in cleanedPosts">
        <Blog :post="post" />
      </div>
    </div>
  </div>
</template>

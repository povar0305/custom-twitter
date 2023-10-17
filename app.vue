<template>
  <NuxtLayout>
    <NuxtPage @updatePost="updatePost"> </NuxtPage>
  </NuxtLayout>
</template>
<script setup>
import { useToast } from "vue-toastification";

function updatePost(post) {
  let posts = JSON.parse(localStorage.getItem("posts"));
  const index = posts.findIndex((n) => n.id === post.id);
  posts[index] = post;
  localStorage.setItem("posts", JSON.stringify(posts));
  useToast().success("Запись обновлена");
}
</script>
<style>
@import url("https://fonts.googleapis.com/css2?family=Raleway:wght@100;400;700&display=swap");

#app {
  font-family: "Raleway", sans-serif;
  padding: 2rem;
}
</style>

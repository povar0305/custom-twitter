<template>
  <v-app id="app">
    <h2>Личный дневник</h2>
    <v-form validate-on="submit lazy" @submit.prevent="chechForm">
      <v-text-field
        focused
        v-model="title"
        variant="outlined"
        density="compact"
        label="Заголовок"
      ></v-text-field>
      <v-textarea
        label="Краткое описание"
        v-model.trim="text"
        density="compact"
        variant="outlined"
      ></v-textarea>
      <v-textarea
        label="Полное описание"
        v-model.trim="fillText"
        density="compact"
        variant="outlined"
      ></v-textarea>
      <v-btn type="submit" block class="mt-2" text="Записать"></v-btn>
    </v-form>
    {{ text }}
    {{ title }}{{ fillText }}
    <v-col>
      <v-post v-for="(post, i) of posts" :key="i" :post="post" />
    </v-col>
  </v-app>
</template>

<script setup>
import VPost from "./components/v-post.vue";

import { ref, computed } from "vue";

let posts = ref([]);

let title = ref();
let text = ref();
let fillText = ref();
function chechForm() {
  let post = {
    text: text.value,
    title: title.value,
    date: new Date(Date.now()).toLocaleString(),
    fillText: fillText.value,
    сomments: [],
  };
  posts.value.push(post);
  localStorage.setItem("posts", JSON.stringify(posts.value));
  text.value = "";
  title.value = "";
  fillText.value = "";
}

function getPosts() {
  console.log("getPosts");
  posts = computed(() => {
    return localStorage.getItem("posts");
  });
}
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Raleway:wght@100;400;700&display=swap");

#app {
  font-family: "Raleway", sans-serif;
  padding: 2rem;
}

.form {
  max-width: 450px;
  width: 100%;
}
</style>

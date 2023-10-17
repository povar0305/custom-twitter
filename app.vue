<template>
  <v-app id="app">
    <h2>Личный дневник</h2>
    <v-form
      ref="form"
      lazy-validation
      validate-on="input"
      @submit.prevent="checkForm()"
    >
      <v-text-field
        v-model="title"
        variant="outlined"
        density="compact"
        label="Заголовок"
        :rules="[
          (v) => !!v || 'Заполните заголовок',
          (v) => (v && v.length <= 50) || 'Максимальная длина заголовка 50',
        ]"
        :counter="50"
        required
      ></v-text-field>
      <v-textarea
        label="Краткое описание"
        v-model.trim="text"
        density="compact"
        variant="outlined"
        :rules="[
          (v) => !!v || 'Заполните краткое описание',
          (v) => (v && v.length <= 100) || 'Максимальная длина описания 100',
        ]"
        :counter="100"
        required
      ></v-textarea>
      <v-textarea
        label="Полное описание"
        v-model.trim="fillText"
        density="compact"
        variant="outlined"
      ></v-textarea>
      <v-btn type="submit" block class="mt-2" text="Записать"></v-btn>
    </v-form>
    <v-col>
      <v-post
        v-for="post of posts"
        :key="post.id"
        :post="post"
        @deletePost="deletePost"
      />
    </v-col>
  </v-app>
</template>

<script setup>
import VPost from "./components/v-post.vue";
import { useToast } from "vue-toastification";

import { ref, onMounted } from "vue";

let posts = ref([]);

let title = ref();
let text = ref();
let fillText = ref();

let form = ref();

function checkForm() {
  form.value?.validate().then(({ valid: isValid }) => {
    if (isValid) {
      let post = {
        id: Object.keys(posts.value).length,
        text: text.value,
        title: title.value,
        date: new Date(Date.now()).toLocaleString(),
        fillText: fillText.value,
        сomments: [],
      };
      posts.value.push(post);
      localStorage.setItem("posts", JSON.stringify(posts.value));
      useToast().success("Запись добавлена", {
        position: "bottom-left",
        hideProgressBar: true,
        timeout: false,
      });
      text.value = "";
      title.value = "";
      fillText.value = "";
      form.value?.resetValidation();
    }
  });
}

function deletePost(deletedPost) {
  posts.value.splice(deletedPost.id, 1);
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

<template>
  <div>
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
        ></v-textarea>
        <v-textarea
          label="Полное описание"
          v-model.trim="fillText"
          density="compact"
          variant="outlined"
          :rules="[
            (v) => v.length < 255 || 'Максимальная длина полного описание 255',
          ]"
          :counter="255"
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
  </div>
</template>

<script setup>
import VPost from "~/components/v-post.vue";
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
        id: posts.value.length + 1,
        text: text.value,
        title: title.value,
        date: new Date(Date.now())
          .toLocaleString()
          .split(",")[0]
          .replace(/\./g, "/"),
        fillText: fillText.value,
        сomments: [],
      };
      posts.value.push(post);
      localStorage.setItem("posts", JSON.stringify(posts.value));

      text.value = "";
      title.value = "";
      fillText.value = "";
      form.value?.resetValidation();
      useToast().success("Запись добавлена");
    } else {
      useToast().error("Заполните корректно форму");
    }
  });
}

function deletePost(deletedPost) {
  const index = posts.value.findIndex((n) => n.id === deletedPost.id);
  if (index !== -1) {
    posts.value.splice(index, 1);
  }
  localStorage.setItem("posts", JSON.stringify(posts.value));
}

onMounted(() => {
  if (localStorage.getItem("posts")) {
    posts.value = JSON.parse(localStorage.getItem("posts"));
  }
});
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Raleway:wght@100;400;700&display=swap");

#app {
  font-family: "Raleway", sans-serif;
  padding: 2rem;
}
</style>

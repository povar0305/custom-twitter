<template>
  <v-card class="pa-1 ma-1">
    <v-card-item>
      <v-card-subtitle class="d-flex justify-space-between align-center"
        >{{ post.date.split(",")[0] }}
        <v-btn
          size="small"
          v-show="!showEdit"
          @click="showEdit = true"
          icon="mdi-pen"
          variant="plain" /><v-btn
          size="small"
          v-show="showEdit"
          @click="$emit('updatePost', post), (showEdit = false)"
          icon="mdi-check"
          variant="plain"
      /></v-card-subtitle>

      <v-card-title class="row d-flex justify-space-between pa-2">
        <p v-show="!showEdit">
          {{ post.title }}
        </p>
        <v-text-field
          v-show="showEdit"
          v-model="post.title"
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
      </v-card-title>
    </v-card-item>
    <v-card-text>
      <p v-show="!showEdit">{{ post.text }}</p>
      <v-textarea
        v-show="showEdit"
        label="Краткое описание"
        v-model.trim="post.text"
        density="compact"
        variant="outlined"
        :rules="[
          (v) => !!v || 'Заполните краткое описание',
          (v) => (v && v.length <= 100) || 'Максимальная длина описания 100',
        ]"
        :counter="100"
        required
      ></v-textarea>
    </v-card-text>
    <v-card-text>
      <p v-show="!showEdit">{{ post.fillText }}</p>
      <v-textarea
        v-show="showEdit"
        label="Полное описание"
        v-model.trim="post.fillText"
        density="compact"
        variant="outlined"
      ></v-textarea>
    </v-card-text>
  </v-card>
</template>

<script setup>
import { ref } from "vue";
const route = useRoute();
let post = ref();

let showEdit = ref(false);
defineEmits(["updatePost"]);
if (localStorage.getItem("posts")) {
  let posts = JSON.parse(localStorage.getItem("posts"));
  post.value = posts.find((e) => {
    if (e.id == route.params.id) {
      return e;
    }
  });
}

function updatePost(post) {}
</script>

<style lang="scss" scoped></style>

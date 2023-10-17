<template>
  <div>sdfghj</div>
  {{ showEdit }}{{ post }}
  <v-card class="pa-1 ma-1">
    <v-card-item>
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
        <v-btn
          size="small"
          v-show="!showEdit"
          @click="showEdit = true"
          icon="mdi-pen"
          variant="plain"
        /><v-btn
          size="small"
          v-show="showEdit"
          @click="updatePost(post)"
          icon="mdi-check"
          variant="plain"
        />
      </v-card-title>

      <v-card-subtitle>{{ post.date.split(",")[0] }}</v-card-subtitle>
    </v-card-item>
    <v-card-text>
      <p v-show="!showEdit.value">{{ post.text }}</p>
    </v-card-text>
    <v-card-text>
      <p v-show="!showEdit.value">{{ post.fillText }}</p>
    </v-card-text>
  </v-card>
</template>

<script setup>
import { ref } from "vue";
const route = useRoute();
console.log(route.params);
let post = ref();

let showEdit = ref(false);

if (localStorage.getItem("posts")) {
  let posts = JSON.parse(localStorage.getItem("posts"));
  post.value = posts.find((e) => {
    if (e.id == route.params.id) {
      return e;
    }
  });
}
</script>

<style lang="scss" scoped></style>

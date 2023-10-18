<template>
  <div class="pa-3">
    {{ post["сomments"] }}
    <v-card class="pa-1 ma-1">
      <v-card-item>
        <v-card-subtitle class="d-flex justify-space-between align-center"
          >{{ post.date.split(",")[0] }}
          <v-btn
            size="small"
            v-show="!showEdit"
            @click="showEdit = true"
            icon="mdi-pen"
            variant="plain" />
          <v-btn
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
          />
        </v-card-title>
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
              (v) =>
                (v && v.length <= 100) || 'Максимальная длина описания 100',
            ]"
            :counter="100"
          />
        </v-card-text>
        <v-card-text>
          <p v-show="!showEdit">{{ post.fillText }}</p>
          <v-textarea
            v-show="showEdit"
            label="Полное описание"
            v-model.trim="post.fillText"
            density="compact"
            variant="outlined"
          />
        </v-card-text>
      </v-card-item>
    </v-card>

    <h3 class="py-3">Комментарии</h3>

    {{ post.comments }}
    <v-col class="ma-0">
      <v-btn
        size="small"
        variant="tonal"
        @click="addComments"
        prepend-icon="mdi-comment-outline"
      >
        Добавить комментарий {{ showFormAddComments }}
      </v-btn>
      <v-row v-show="showFormAddComments" class="ma-0 py-3">
        {{ name }}
        {{ email }}
        {{ comment }}
        <v-form
          class="formAddComments"
          ref="formAddComments"
          lazy-validation
          validate-on="input"
          @submit.prevent="checkFormAddComments(), $emit('updatePost', post)"
        >
          <v-text-field
            v-model="name"
            variant="outlined"
            density="compact"
            label="Имя"
            :rules="[
              (v) => !!v || 'Введите имя',
              (v) => (v && v.length <= 50) || 'Максимальная длина имени 50',
            ]"
            :counter="50"
          ></v-text-field
          ><v-text-field
            v-model="email"
            variant="outlined"
            density="compact"
            label="Почта"
            :rules="[
              (v) =>
                !v ||
                /^\w+([.-]?\w+)*@\w+([.-]?\w+)*(\.\w{2,3})+$/.test(v) ||
                'Введите корректную почту',
            ]"
            :counter="50"
          ></v-text-field>
          <v-text-field
            v-model="comment"
            variant="outlined"
            density="compact"
            label="Комментарий"
            :rules="[
              (v) => !!v || 'Введите комментарий',
              (v) =>
                (v && v.length <= 255) || 'Максимальная длина комментария 255',
            ]"
            :counter="50"
          ></v-text-field>
          <v-btn size="small" icon="mdi-check" variant="plain" type="submit" />
        </v-form>
      </v-row>
    </v-col>
    <v-card class="my-2">
      <v-card-item>
        <v-card-subtitle class="row d-flex justify-space-between">
          <p>имя (почта)</p>
          <v-btn size="small" icon="mdi-close" variant="plain"
        /></v-card-subtitle>
        <v-card-text>текст</v-card-text>
      </v-card-item>
    </v-card>
  </div>
</template>

<script setup>
import { ref } from "vue";
const route = useRoute();
let post = ref();

let showEdit = ref(false);

let name = ref();
let email = ref();
let comment = ref();
let formAddComments = ref();
let showFormAddComments = ref(false);

defineEmits(["updatePost"]);

if (localStorage.getItem("posts")) {
  let posts = JSON.parse(localStorage.getItem("posts"));
  //TODO изменить дату

  post.value = posts.find((e) => {
    if (e.id == route.params.id) {
      return e;
    }
  });
}

function addComments() {
  showFormAddComments.value = true;
}

function checkFormAddComments() {
  console.log("checkFormAddComments", name.value, email.value, comment.value);
  console.log(post.value["сomments"], typeof post.value["сomments"]);
  post.value["сomments"].push({
    name: name.value,
    email: email.value,
    comment: comment.value,
  });
}
</script>

<style scoped>
.formAddComments {
  display: flex;
  width: 100%;
}
</style>

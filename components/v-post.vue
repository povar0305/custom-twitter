<template>
  <v-card class="pa-2 ma-2">
    <v-card-item>
      <v-card-title>{{ post.title }}</v-card-title>
      <v-card-subtitle>{{ post.date.split(",")[0] }}</v-card-subtitle>
    </v-card-item>
    <v-card-text>{{ post.text }}</v-card-text
    >{{ post.сomments.length }}
    <v-card-actions>
      <v-chip class="ma-2" label text-color="white">
        {{ post.сomments.length }}
        <v-icon icon="mdi-comment-outline"></v-icon>
      </v-chip>
    </v-card-actions>
  </v-card>
</template>

<script setup>
defineProps(["post"]);
</script>
<style>
.card {
  height: auto;
}
</style>

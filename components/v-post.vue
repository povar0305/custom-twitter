<template>
  <v-card class="pa-2 ma-2">
    <v-card-item
      >{{ post }}
      <v-card-title>{{ post.title }}</v-card-title>
      <v-card-subtitle>{{ post.date.split(",")[0] }}</v-card-subtitle>
    </v-card-item>
    <v-card-text>{{ post.text }}</v-card-text>
    <v-badge v-if="post.сomments.length > 0" :content="post.сomments.length">
      <v-icon icon="mdi-comment-outline" />
    </v-badge>
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

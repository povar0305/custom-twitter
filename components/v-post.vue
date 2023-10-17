<template>
  <v-card class="pa-2 ma-2">
    <v-card-item>
      <v-row justify="space-between" class="ma-0">
        <v-card-title>{{ post.title }}</v-card-title>
        <v-btn
          size="x-small"
          @click="$emit('deletePost', post)"
          icon="mdi-close"
          variant="plain"
        >
        </v-btn>
      </v-row>

      <v-card-subtitle>{{ post.date.split(",")[0] }}</v-card-subtitle>
    </v-card-item>
    <v-card-text>{{ post.text }}{{ post }}</v-card-text>
    <v-card-actions>
      <v-row justify="end" class="ma-0">
        <v-badge
          v-if="post.сomments.length > 0"
          :content="post.сomments.length"
        >
          <v-icon icon="mdi-comment-outline" />
        </v-badge>
      </v-row>
    </v-card-actions>
  </v-card>
</template>

<script setup>
defineProps(["post"]);
defineEmits(["deletePost"]);
</script>
<style>
.card {
  height: auto;
}
</style>

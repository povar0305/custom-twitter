<template>
  <NuxtLink :to.prevent="'/posts/' + post.id">
    <v-card class="pa-1 ma-1">
      <v-card-item>
        <v-card-subtitle
          class="row d-flex justify-space-between pa-2 align-center"
          >{{ post.date.replace(/[/]/g, ".")
          }}<v-btn
            size="small"
            @click.prevent="$emit('deletePost', post)"
            icon="mdi-close"
            variant="plain"
        /></v-card-subtitle>

        <v-card-title>
          {{ post.title }}
        </v-card-title>
      </v-card-item>
      <v-card-text>{{ post.text }}</v-card-text>
      <v-card-actions>
        <v-badge
          v-if="post.сomments.length > 0"
          :content="post.сomments.length"
        >
          <v-icon icon="mdi-comment-outline" />
        </v-badge>
      </v-card-actions>
    </v-card>
  </NuxtLink>
</template>

<script setup>
defineProps(["post"]);
defineEmits(["deletePost", "updatePost"]);
</script>
<style scoped>
.card {
  height: auto;
}
.v-card:hover {
  background: #ededff !important;
}
a {
  text-decoration: none;
}
</style>

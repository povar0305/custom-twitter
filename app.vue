<template>
  <div id="app">
    <h2>Личный дневник</h2>
    <form @submit.prevent="chechForm">
      <input
        type="text"
        required
        v-model.trim="title"
        placeholder="Заголовок заметки"
      />
      <textarea
        required
        v-model.trim="text"
        placeholder="Текст заметки"
      ></textarea>

      <button type="submit">Записать</button>
    </form>

    <div>
      <ul>
        <li v-for="(post, i) of posts" :key="i">
          {{ post }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
  data: function () {
    return {
      text: "",
      title: "",
      posts: [
        {
          text: "hello",
          title: null,
          date: Date,
        },
      ],
    };
  },
  methods: {
    chechForm() {
      console.log("input_text", this.text);
      this.posts.push({
        text: this.text,
        title: this.title,
        date: new Date(Date.now()).toLocaleString(),
      });
      this.text = "";
      this.title = "";
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Raleway:wght@100;400;700&display=swap");

#app {
  font-family: "Raleway", sans-serif;
}
</style>

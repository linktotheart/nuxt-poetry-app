<template>
  <div class="container">
    <h1 class="title">Poems</h1>
    <blockquote>
      <h2>{{ randomPoem[0].title }}</h2>
      <hr />
      <p :key="i" v-for="(line, i) in randomPoem[0].lines">{{ line }}</p>
      <br />
      <br />
      <br />

      <em
        ><strong> {{ randomPoem[0].author }} </strong></em
      >
    </blockquote>
  </div>
</template>

<script>
export default {
  async asyncData() {
    const randomPoem = await fetch("https://poetrydb.org/random").then((res) =>
      res.json()
    );

    return { randomPoem };
  },
  data() {
    return {
      randomPoem: null,
    };
  },
};
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
}
</style>

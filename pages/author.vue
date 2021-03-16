<template>
  <div class="container padding-top-large">
    <h1 class="title">Poems</h1>
    <div>
      <h2>{{ title }}</h2>
      <div class="section padding-large shadow">
        <ul>
          <li v-for="author in authors.authors" :Key="author" v-html="author" />
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData() {
    const authors = await fetch("https://poetrydb.org/author").then((res) =>
      res.json()
    );

    return { authors };
  },
  data() {
    return {
      authors: {
        authors: null,
      },
      title: "By Authors",
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
  text-align: left !important;
}
.section {
  max-width: 660px;
  width: 100%;
}
</style>

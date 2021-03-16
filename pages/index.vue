<template>
  <div class="container padding-top-large">
    <h1 class="title">Poems</h1>
    <div>
      <h2>{{ randomPoem[0].title }}</h2>
      <hr />
      <p>
        <span :key="i" v-for="(line, i) in randomPoem[0].lines">
          {{ line }} <br />
        </span>
      </p>

      <hr class="margin-top-large" />

      <em
        ><strong> {{ randomPoem[0].author }} </strong></em
      >
    </div>
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

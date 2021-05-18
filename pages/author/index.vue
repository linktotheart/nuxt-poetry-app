<template>
  <div class="container mt-4">
    <div>
      <h2 class="text-center ">Peoms {{ title }}</h2>
      <div class="section padding-large shadow">
        <ul class="row row-cols-lg-4">
          <li class="card " v-for="(author, i) in authors.authors" :Key="i">
            <div class="card-body">
              <nuxt-link class="" :to="'author/' + author"> {{ author }} </nuxt-link>
            </div>
          </li>
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


</style>

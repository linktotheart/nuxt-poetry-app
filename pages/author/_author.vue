<template>
  <div class="container">
    <h1>Author name: {{ $route.params.author }}</h1>

    <div class="section padding">
      <div class="card margin-bottom" v-for="item in authorName" :key="item">
        <div class="card-body">
          <h4 class="card-title">
            {{ item.title }}
          </h4>
          <h5 class="card-subtitle">{{ item.linecount }} Lines</h5>
          <!-- <p class="card-text">This is another example of a card without image. Cards are also meant to be used without images, but with text/links/buttons.</p> -->
          <nuxt-link class="paper-btn btn-small margin-top-small button" 
          :to="'/poems/' + item.title"
            >Read More
          </nuxt-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ params }) {
    const authorName = await fetch(
      "https://poetrydb.org/author/" + params.author + "/title,linecount"
    ).then((res) => res.json());
    console.log(params.author);
    return { authorName };
  },
  data() {
    return {
      author: null,
      authorName: null,
    };
  },
};
</script>
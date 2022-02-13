<template>
  <div class="container mt-5">
    <h1 class="text-center">{{ $route.params.author.replaceAll("_", " ") }}</h1>

    <section class="row mt-5">
      <div class="col-12 mb-4">
        <div class="form col-md-6 mx-auto">
          <div class="input-group mb-3">
            <div class="input-group-prepend">
              <span class="input-group-text" id="basic-addon1">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="16"
                  height="16"
                  fill="currentColor"
                  class="bi bi-search"
                  viewBox="0 0 16 16"
                >
                  <path
                    d="M11.742 10.344a6.5 6.5 0 1 0-1.397 1.398h-.001c.03.04.062.078.098.115l3.85 3.85a1 1 0 0 0 1.415-1.414l-3.85-3.85a1.007 1.007 0 0 0-.115-.1zM12 6.5a5.5 5.5 0 1 1-11 0 5.5 5.5 0 0 1 11 0z"
                  />
                </svg>
              </span>
            </div>
            <input
              type="text"
              name=""
              id=""
              v-model="searchQ"
              placeholder="search poems ..."
              class="form-control form-control-lg rounded-pill"
            />
            <!-- <input type="text" class="form-control" placeholder="Username" aria-label="Username" aria-describedby="basic-addon1"> -->
          </div>
        </div>
      </div>
      <template>
        <article
          class="col-lg-4 col-md-6"
          v-for="item in filteredPoems"
          :key="item"
        >
          <div class="card shadow-sm mb-5">
            <div class="card-body">
              <h4 class="card-title mb-4">
                {{ item.title }}
              </h4>
              <h5 class="badge badge-primary d-inline small mb-0">
                {{ item.linecount }} Lines
              </h5>
              <!-- <p class="card-text">This is another example of a card without image. Cards are also meant to be used without images, but with text/links/buttons.</p> -->
            </div>
            <div class="card-footer">
              <nuxt-link class="btn py-2 px-4" :to="'/poems/' + item.title"
                >Read More
              </nuxt-link>
            </div>
          </div>
        </article>
      </template>
    </section>
  </div>
</template>

<script>
export default {
  async asyncData({ params }) {
    console.log(params);
    const authorName = await fetch(
      "https://poetrydb.org/author/" +
        params?.author?.replaceAll("_", " ") +
        "/title,linecount"
    ).then((res) => res.json());
    console.log(params.author);
    return { authorName };
  },
  data() {
    return {
      searchQ: "",
      author: null,
      authorName: null,
    };
  },
  computed: {
	filteredPoems() {
	  return this.authorName.filter((poem) => {
		return poem.title.toLowerCase().includes(this.searchQ.toLowerCase());
	  });
	},
  },
};
</script>

<style scoped>
.card {
  height: calc(100% - 2rem);
}
</style>

<template>
  <div class="container mt-5">
    <h2 class="text-center">Poems {{ title }}</h2>
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
              placeholder="search authors ..."
              class="form-control form-control-lg rounded-pill"
            />
            <!-- <input type="text" class="form-control" placeholder="Username" aria-label="Username" aria-describedby="basic-addon1"> -->
          </div>
        </div>
      </div>
      <article
        class="col-lg-4 mb-4 col-md-6 col-sm-12"
        v-for="(author, i) in filteredAuthors"
        :Key="i"
      >
        <!-- <div class="card rounded-lg">
                  <div class="card-body"> -->
        <nuxt-link
          v-bind:title="author"
          class="btn py-3 btn-lg btn-block w-100 text-truncate btn-outline-info"
          :to="'author/' + author.replaceAll(' ', '_')"
        >
          {{ author }}
        </nuxt-link>
        <!-- </div>
              </div> -->
      </article>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      authors: [],
      title: "By Authors",
      searchQ: "",
    };
  },
  computed: {
    filteredAuthors() {
      return this.authors.filter((author) => {
        return author.toLowerCase().includes(this.searchQ.toLowerCase());
      });
    },
  },
  async fetch() {
    const {authors} = await fetch("https://poetrydb.org/author").then((res) =>
      res.json()
    );
    // console.log({ authors })
    this.authors = authors;
  },
};
</script>

<style lang="scss" scoped>
.btn {
  transition: 0.35s ease-in-out background, 0.3s ease color;
  &:hover {
    background: #07f;
    color: #fff;
  }
}
</style>

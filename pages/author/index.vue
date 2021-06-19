<template>
  <div class="container mt-5">
      <h2 class="text-center">Poems {{ title }}</h2>
          <section class="row mt-5">
            <article class="col-lg-4 mb-4 col-md-6 col-sm-12"  v-for="(author, i) in authors.authors" :Key="i">
                <!-- <div class="card rounded-lg">
                  <div class="card-body"> -->
                    <nuxt-link  v-bind:title={author} class="btn py-3 btn-lg btn-block w-100 text-truncate btn-outline-info" :to="'author/' + author"> 
                      {{ author }}   </nuxt-link>
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
      authors: {
      },
      title: "By Authors",
    };
  },
  async fetch() {

    const authors = await fetch("https://poetrydb.org/author")
    .then(res => res.json());  
    // console.log({ authors })
    this.authors = authors
  },
};
</script>

<style lang="scss" scoped> 
.btn{
  transition: .35s ease-in-out background, 0.3s ease color;
  &:hover{
    background: #07f;
    color: #fff;
  }
}

</style>

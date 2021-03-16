<template>
  <div class="container">

    <div class="card shadow shadow-large padding margin-top-large ">
      
      <article class="article">
         <h1 class="article-title"><a href="">{{poem.title}}</a></h1>
         <p class="article-meta">Written by 
            <nuxt-link :to="'/author/' + poem.author">
               {{poem.author}}
            </nuxt-link>
         </p>
         <p> 
            <span v-for="(line, idx) in poem.lines" :key="idx">
               {{line}} <br>
            </span>
         </p>
      
      

         <div class="row">
            <button>Read More</button>
            
            
         </div>
      </article>

    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ params }) {
    const poem = await fetch(
      "https://poetrydb.org/title/" + params.title
    ).then((res) => res.json());
    return {
       poem: poem[0]
    };
  },
  data() {
    return {
      poem: {},
      // authorName: null,
    };
  },
};
</script>
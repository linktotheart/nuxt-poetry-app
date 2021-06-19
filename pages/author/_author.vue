<template>
	<div class="container mt-5">
		<h1 class="text-center "> {{ $route.params.author }}</h1>

		<section class="row mt-5">
			<article
				class="col-lg-4 col-md-6"
				v-for="item in authorName"
				:key="item"
			>
				<div class="card shadow-sm mb-5">
					<div class="card-body">
						<h4 class="card-title mb-4">
							{{ item.title }}
						</h4>
						<h5 class="badge badge-primary d-inline small mb-0">{{ item.linecount }} Lines</h5>
						<!-- <p class="card-text">This is another example of a card without image. Cards are also meant to be used without images, but with text/links/buttons.</p> -->
						
					</div>
          <div class="card-footer">
            <nuxt-link
							class="btn py-2 px-4"
							:to="'/poems/' + item.title"
						>Read More
						</nuxt-link>
          </div>
				</div>
			</article>
		</section>
	</div>
</template>

<script>
export default {
	async asyncData({ params }) {
		const authorName = await fetch(
			"https://poetrydb.org/author/" + params.author + "/title,linecount"
		).then(res => res.json());
		console.log(params.author);
		return { authorName };
	},
	data() {
		return {
			author: null,
			authorName: null
		};
	}
};
</script>

<style scoped>
.card{
  height: calc(100% - 2rem);
}
</style>
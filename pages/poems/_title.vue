<template>
	<div class="container">

	<div class="mt-5 mb-5 ">
     

		<div class="alert alert-info py-5 d-flex justify-content-center 	"  v-if="pending">
			<div class="spinner-border" style="width: 3rem; height: 3rem;" role="status">
			<!-- <span class="sr-only">Loading...</span> -->
			</div>
		</div>
		<article v-else  class="card bg-white shadow">
			<div class="article col-xl- col-lg-7 mx-auto col-md-9 col-sm-11 py-5 px-4 px-md-5">
				<h1 class="title mb-4">{{poem.title}}</h1>
				<p class="text-muted ">Written by
					<nuxt-link
						class="text-muted"
						:to="'/author/' + poem.author"
					>
						{{poem.author}}
					</nuxt-link>
				</p>
				<p class="
		my-4">
					<span
						v-for="(line, idx) in poem.lines"
						:key="idx"
					>
						{{line}} <br>
					</span>
				</p>
				<hr class="my-5">
				<nuxt-link
					:to="'/author/' + poem.author"
					class="btn px-4 py-2"
				>
					<svg
						xmlns="http://www.w3.org/2000/svg"
						width="16"
						height="16"
						fill="currentColor"
						class="bi mr-3 align-middle bi-arrow-left"
						viewBox="0 0 16 16"
					>
						<path
							fill-rule="evenodd"
							d="M15 8a.5.5 0 0 0-.5-.5H2.707l3.147-3.146a.5.5 0 1 0-.708-.708l-4 4a.5.5 0 0 0 0 .708l4 4a.5.5 0 0 0 .708-.708L2.707 8.5H14.5A.5.5 0 0 0 15 8z"
						/>
					</svg>
					Go Back
				</nuxt-link>
			</div>
		</article>

	</div>
	</div>
</template>

<script>
export default {
	// async fetch({ params }) {
	// 	const poem = await fetch(
	// 		"https://poetrydb.org/title/" + params.title
	// 	).then(res => res.json());
	// 	this.poem = poem;
	// 	console.log(poem);
	// },
	data() {
		return {
			poem: {},
			pending: true,
			// authorName: null,
		};
	},
	methods: {
		async fetchPoem() {
			this.pending = true
			const [poem] = await fetch("https://poetrydb.org/title/" + this.$route.params.title)
				.then(res => res.json())
				.catch(err => {
					this.pending = false
					console.log(err)
				})		
			console.log(poem);
			this.poem = poem;
			this.pending = false
		}
	},
	async mounted() {
		await this.fetchPoem()
	}
	
};
</script>
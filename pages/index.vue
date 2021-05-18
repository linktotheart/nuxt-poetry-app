<template>
	<div class="main-wrapper">
		<Hero />

		<div class="container sec-hero mb-4">
			<div class="row">
				<div class="col-md-6">
          <div class="card justify-content-center py-4 mb-4 align-items-center bg-info bg-gradient h-100">
            <h2 class="display-4 font-weight-bolder text-white fw-bold  ">
            Poem <br>
            of the  <br>
            Day 
            </h2>
          </div>
				</div>
				<div class="col-xl-6 col-md-6">
					<div class="card mb-4 h-100">
						<div class="card-body">
							<h4 class="card-title">
							{{ randomPoem[0].title }}
							</h4>
							<p class="card-text">
								<span
									:key="i"
									v-for="(line, i) in randomPoem[0].lines.slice(0, 5)"
								>
									{{ line }} <br />
								</span>
								<span>...</span>
								<span>...</span>
								<span>...</span>
							</p>
							<div class="d-flex align-items-center  justify-content-between">
                <nuxt-link
								class="btn btn-block  btn-secondary text-decoration-none"
								:to="`/poems/${randomPoem[0].title}`"
							>
								Read More
							</nuxt-link>

							<em><strong> -- {{ randomPoem[0].author }} </strong></em>
              </div>
						</div>

					</div>

				</div>
			</div>

      <div class="row mt-4">
        <div class="col-md-6">
          <div class="card bg-light  p-4">
            <img src="~/assets/img/03.png" alt="png " class="img-fluid">
          </div>
        </div>
        <div class="col-md-6">
          <div class="card justify-content-center  mb-4 align-items-center bg-warning  bg-gradient h-100">
            <h2 class="h1 py-5 font-weight-bolder text-center  text-dark fw-bold  ">
              View All <br> Authors 
            </h2>
            <p>
              <nuxt-link to="/author" class="btn btn-warning">See All Authors</nuxt-link>
            </p>
          </div>
				</div>
      </div>
		</div>

    <footer class="mt-5 pt-5 border-top border-light pb-4 bg-gradient">
        <p class="mb-0 text-muted text-center ">
          Made by <a href="https://github.com/linktotheart/">Pulkit Singh</a> in <a href="https://nuxtjs.org/">NuxtJS</a>
        </p>
      
    </footer>
	</div>
</template>

<script>
export default {
	async asyncData() {
		const randomPoem = await fetch(
			"https://poetrydb.org/random"
		).then(res => res.json());

		return { randomPoem };
	},
	data() {
		return {
			randomPoem: null
		};
	}
};
</script>

<style>
</style>

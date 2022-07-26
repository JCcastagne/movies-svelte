<script context="module">
	export async function load({ fetch }) {
		const URL_PREFIX = `https://api.themoviedb.org/3/movie`
		const URL_SUFFIX = `/popular`
		const API_KEY = `?api_key=2c3b4fc9641a33b8ac343629843d4e90&language=en-US`

		const res = await fetch(`${URL_PREFIX}${URL_SUFFIX}${API_KEY}`)
		const data = await res.json()
		if (res.ok) {
			return {
				props: { popular: data.results }
			}
		}
	}
</script>

<script>
	import PopularMovies from '../components/PopularMovies.svelte'
	export let popular
</script>

<section>
	<div class="container">
		<PopularMovies movies={popular} />
	</div>
</section>

<style>
	section {
		width: 100vw;
		min-height: 100vh;
		padding: 10vh 10vw;

		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}

	.container {
		max-width: 1500px;
		width: 100%;
	}
</style>

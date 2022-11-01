<script context="module">
	export async function load({ fetch, params }) {
		const URL_PREFIX = `https://api.themoviedb.org/3/search`
		const URL_SUFFIX = `/movie`
		const API_KEY = `?api_key=2c3b4fc9641a33b8ac343629843d4e90&language=en-US`
		const searchValue = `&query=${params.id}&page=1&include_adult=false`

		const res = await fetch(`${URL_PREFIX}${URL_SUFFIX}${API_KEY}${searchValue}`)
		const data = await res.json()
		if (res.ok) {
			console.log(data.results)
			return {
				props: { searchedMovie: data.results }
			}
		}
	}
</script>

<script>
	import MovieCard from '../../components/MovieCard.svelte'
	import Nav from '../../components/Nav.svelte'
	export let searchedMovie
</script>

<section>
	<div class="container">
		<Nav />
		<div class="searched-movies">
			{#each searchedMovie as movie}
				<MovieCard {movie} />
			{/each}
		</div>
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

	.searched-movies {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
		grid-column-gap: 1em;
		grid-row-gap: 2.33em;
	}
</style>

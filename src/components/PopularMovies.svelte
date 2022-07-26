<script>
	export let movies
	import MovieCard from './MovieCard.svelte'
</script>

<h3>popular movies</h3>

<div class="popular-movies">
	{#each movies as movie}
		<MovieCard {movie} />
	{/each}
</div>

<style>
	h3 {
		font-size: 2em;
	}

	.popular-movies {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
		grid-column-gap: 1em;
		grid-row-gap: 2em;

		border: 1px solid red;
	}
</style>

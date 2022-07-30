<script>
	import SearchMovies from './SearchMovies.svelte'

	import tmdb_primary_blue_square_alt from '../public/img/tmdb_primary_blue_square_alt.svg'
</script>

<nav>
	<a href="/">
		<img src={tmdb_primary_blue_square_alt} alt="the movie database logo" class="logo" />
	</a>
	<SearchMovies />
</nav>

<style>
	nav {
		display: flex;
		flex-wrap: wrap;
		justify-content: center;
		align-items: center;
		margin-bottom: 5em;
	}

	.logo {
		height: calc(2.75em + 8px);
		transform: translateY(4px);
		margin-right: 1em;
	}
</style>

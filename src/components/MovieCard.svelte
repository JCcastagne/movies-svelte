<script>
	export let movie
</script>

<div class="movie-card">
	<img
		src={`https://image.tmdb.org/t/p/w500${movie.poster_path}`}
		alt={`Poster for ${movie.title}`}
	/>
	<div class="description">
		<h2>{movie.title}</h2>
		<p>{movie.release_date}</p>
	</div>
</div>

<style>
	.movie-card {
		display: flex;
		flex-direction: column;
	}

	img {
		width: 100%;
		height: 100%;
		object-fit: cover;

		border-radius: 1em;
		margin-bottom: 1em;
	}

	.description h2 {
		font-size: calc(2em * 0.66);
		font-weight: 500;
		margin-bottom: calc(2em * 0.165);
	}

	.description p {
		font-size: 1em;
		font-weight: 400;
	}
</style>

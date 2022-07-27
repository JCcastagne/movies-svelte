<script context="module">
	export async function load({ fetch, params }) {
		const URL_PREFIX = `https://api.themoviedb.org/3/movie`
		const URL_SUFFIX = `/${params.id}`
		const API_KEY = `?api_key=2c3b4fc9641a33b8ac343629843d4e90&language=en-US`

		const res = await fetch(`${URL_PREFIX}${URL_SUFFIX}${API_KEY}`)
		const movieDetail = await res.json()
		if (res.ok) {
			console.log(movieDetail)
			return {
				props: { movieDetail }
			}
		}
	}
</script>

<script>
	export let movieDetail
</script>

<section>
	<div class="container">
		<button class="back-button"><a href="/">&#9700;</a></button>

		<div class="movie-detail">
			<img
				src={`https://image.tmdb.org/t/p/original${movieDetail.backdrop_path}`}
				alt={`${movieDetail.title}`}
			/>
			<div class="text-container">
				<h1>{movieDetail.title}</h1>
				<div class="sub-title">
					<p>{`${movieDetail.genres[0].name} & ${movieDetail.genres[2].name}`}</p>
					<h2>&#11089; {movieDetail.vote_average}</h2>
				</div>
				<p>{movieDetail.overview}</p>
				<p>
					{`Released on ${new Date(movieDetail.release_date).toLocaleDateString('en-US', {
						weekday: 'long',
						year: 'numeric',
						month: 'long',
						day: 'numeric'
					})}`}
				</p>
				<a href={`${movieDetail.homepage}`} target="_blank">Go to website &#10095;</a>
			</div>
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

	.back-button {
		background-color: transparent;
		border: none;
		transform: translate(-2.33em, -2.33em) rotate(-45deg);
		margin-bottom: 1em;
		position: absolute;
		transition: all ease-in-out 0.2s;
	}
	.back-button a:link,
	.back-button a:visited,
	.back-button a:active {
		text-decoration: none;
		color: #c6d2de;
		font-size: 1em;
		font-size: 1.33em;
		font-weight: 600;
	}
	button:hover {
		transform: translate(-2.33em, -2.33em) rotate(-45deg) scale(1.5);
		transform-origin: 50%, 50%;
	}

	.movie-detail {
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	img {
		width: 100%;
		height: 100%;
		min-height: 33vh;
		object-fit: cover;

		border-radius: 1em;
	}

	h1 {
		max-width: 66%;
		font-size: clamp(2.66em, 5vw, 6em);
		line-height: 1.33em;
		padding: 0.33em 0.5em;
		font-weight: 600;
		position: absolute;
		transform: translateY(-100%);
		color: white;
		text-shadow: 0 8px 17px rgba(0, 0, 0, 0.42);
		text-transform: uppercase;
	}

	.sub-title {
		padding: 1em 0;
		display: flex;
		align-items: center;
		widows: 100%;
		justify-content: space-between;
	}

	.sub-title h2 {
		font-size: calc(2em);
		font-weight: 500;
		margin-bottom: calc(2em * 0.165);
	}

	.sub-title p {
		font-size: calc(2em * 0.66);
		opacity: 0.66;
		font-weight: 500;
		margin-bottom: calc(2em * 0.165);
	}

	.text-container > p {
		font-size: 1em;
		font-weight: 400;
		margin-bottom: 1em;
	}
	.text-container > p:nth-of-type(2) {
		opacity: 0.66;
	}

	.text-container > a,
	.text-container > a:link,
	.text-container > a:visited,
	.text-container > a:active {
		display: flex;
		justify-content: flex-end;
		width: 100%;
		text-align: right;
		text-decoration: none;
		color: #90cea19e;
		font-size: 1em;
	}
</style>

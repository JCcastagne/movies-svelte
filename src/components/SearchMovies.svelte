<script>
	let searchInputValue = ''
	import chevron_right_white from '../public/img/chevron-right-white.png'

	let searchInputActive = false

	function toggleSearchInputActiveState() {
		searchInputActive ? (searchInputActive = false) : (searchInputActive = true)
	}
</script>

<form class="search">
	<input
		bind:value={searchInputValue}
		name="search_movie"
		type="text"
		placeholder="Search movie"
		on:focus={toggleSearchInputActiveState}
		on:blur={toggleSearchInputActiveState}
	/>
	<button class={searchInputActive ? 'active' : ''} for="search_movie">
		{searchInputActive ? 'Search' : ' '}
		<img src={chevron_right_white} alt="chevron arrow" />
	</button>
</form>

<style>
	form {
		display: flex;
		align-items: center;
		justify-content: flex-end;

		background: linear-gradient(270deg, #8ecea2 0%, #03b4e4 100%),
			linear-gradient(0deg, #ffffff, #ffffff);
		padding: 3px;
		border-radius: 99px;
	}

	input,
	button {
		height: 3em;
		font-family: 'Poppins';
		font-size: 16px;
		font-weight: 400;
		padding: 0;
		margin: 0;
		border: none;
	}

	input {
		padding: 0.5em 1em;
		background-color: white;
		color: #13253f;
		border-radius: 99px;
		width: clamp(250px, 50vw, 500px);
	}
	input::placeholder {
		color: #13253fa8;
	}
	input:focus {
		border: none;
		outline: none;
	}

	button {
		position: absolute;
		transform: translate(-3px, 0);
		height: calc(3em - 6px);
		width: calc(3em - 6px);
		display: flex;
		align-items: center;
		justify-content: center;
		cursor: pointer;

		color: rgba(255, 255, 255, 0);
		background: #1cb9d9;
		box-shadow: 0px 8px 16px rgba(16, 102, 119, 0.65);
		border-radius: 99px;

		transition: 0.2s ease-in;
		transition-property: width, color;
	}

	button.active {
		padding-left: 1em;
		width: 7em;
		color: rgb(255, 255, 255);
	}
	button.active img {
		padding-left: 0.5em;
		padding-right: 0.8em;
	}
</style>

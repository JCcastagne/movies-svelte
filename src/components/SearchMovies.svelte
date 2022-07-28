<script>
	let searchInputValue = ''
</script>

<form class="search">
	<label for="search_movie">Search movie</label>
	<input bind:value={searchInputValue} name="search_movie" type="text" />
	<button>Search</button>
</form>

<script>
	import ytdl from 'ytdl-core'; 
	import fs from 'fs';

	export let name;
	let url;

	function handleClick() {
		console.log(`URL: ${url}`);
		const video = ytdl(url, {
			quality: "highestaudio",
			format: "mp3",
			filter: "audioonly"
		});
//		video.pipe(fs.createWriteStream("test.mp3"));
	}
</script>

<main>
	<h1>Hello {name}!!</h1>
	<input bind:value={url} placeholder="enter video url">
	<button on:click={handleClick}>Scarica</button>
</main>

<style>

	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
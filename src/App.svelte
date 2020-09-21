<script>
import Card from './components/Card.svelte';
import Button from './components/Button.svelte';
import axios from 'axios';

let showAPI = false;
const _API = 'https://api.publicapis.org';

let API = {};

const handleClick = () => {
	axios.get(`${_API}/random?auth=null`)
		.then((answer) => {
			// handle success
			const response = answer.data.entries[0];

			// save response to API object
			API = response;

			// show card
			showAPI = true;

			console.log(response);
			console.log('obiekt api:');
			console.log(API);
		})
		.catch((error) => {
			// handle error
			console.log(error);
		});
};
</script>

<main class="home">
	<Button text="Random API" on:click={handleClick}/>

	{#if showAPI}
		<Card data={API} />
	{/if}
</main>

<style type="text/scss">
.home {
	// display: flex;
	// width: 100vw;
	// height: 100vh;
	// align-items: flex-end;
	// justify-content: center;
}
</style>
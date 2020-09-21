<script>
import Card from './components/Card.svelte';
import Button from './components/Button.svelte';
import axios from 'axios';

let showAPI = false;
const API = 'https://api.publicapis.org';

const handleClick = () => {
	axios.get(`${API}/random?auth=null`)
		.then((answer) => {
			// handle success
			const response = answer.data.entries[0];
			console.log(response);
		})
		.catch((error) => {
			// handle error
			console.log(error);
		});
};
</script>

<main class="home">
	{#if showAPI}
		<Card />
	{/if}

	<Button text="Get random API  🎲" on:click={handleClick}/>
	<Button text="Search  🔍" type="secondary" />
</main>

<style type="text/scss">
.home {
	display: flex;
	width: 100vw;
	height: 100vh;
	align-items: center;
	justify-content: center;
}
</style>
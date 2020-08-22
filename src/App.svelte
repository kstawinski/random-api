<script>
import Card from './components/Card.svelte';
import Button from './components/Button.svelte';

let showAPI = false;

const handleClick = () => {
	showAPI = !showAPI;
};
</script>

<main class="home">
	{#if showAPI}
		<Card />
	{/if}

	<Button text="Get random API  🎲" on:click={handleClick}/>
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
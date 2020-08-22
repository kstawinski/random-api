<script>
import Button from './components/Button.svelte';

const handleClick = () => {
	alert('clicked');
};
</script>

<main>
	<Button text="Get random API  🎲" on:click={handleClick}/>
</main>

<style type="text/scss">
main {
	display: flex;
	width: 100vw;
	height: 100vh;
	align-items: center;
	justify-content: center;
}
</style>
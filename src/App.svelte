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
	<div class="container container__flex">
		<section class="sidebar">
			<label for="search" class="sidebar__label">Search query</label>
			<input type="search" id="search" class="sidebar__input">

			<label for="category" class="sidebar__label">Category</label>
			<select id="category" class="sidebar__input">
				<option value="volvo">Animals</option>
				<option value="volvo">Food & Drinks</option>
				<option value="volvo">Development</option>
				<option value="volvo">Funny</option>
			</select>

			<div class="container__flex">
				<input type="checkbox" id="https" class="sidebar__input">
				<label for="https" class="sidebar__label">HTTPS</label>
			</div>

			<div class="container__flex">
				<input type="checkbox" id="cors" class="sidebar__input">
				<label for="cors" class="sidebar__label">Cors</label>
			</div>
		<Button text="Search" on:click={handleClick}/>
		<Button text="Give me a random API" type="secondary" on:click={handleClick}/>
		</section>
		<div>
			{#if showAPI}
				<Card data={API} />
			{/if}
		</div>
	</div>
</main>

<style type="text/scss">
.home {
	display: flex;
	width: 100vw;
	height: 100vh;
	margin: 0 auto;
	align-items: center;
	justify-content: center;
}

.container {
	width: 80%;
	margin: 0 auto;

	&__flex {
		display: flex;
		justify-content: flex-start;
	}
}

.sidebar {
  box-shadow: 0 1px 3px rgba(0,0,0,0.12), 0 1px 2px rgba(0,0,0,0.24);
	padding: 25px;
	width: 20%;

	&__label {
		display: block;
		margin-bottom: 7px;
    font-weight: 500;
	}
	&__input {
		width: 100%;
    border: 0;
    padding: 10px;
    font-size: inherit;
    font-family: inherit;
    background: #e4e4e469;
    border: 1px solid #dcdcdc;
    border-radius: 6px;

		&:not(:last-child) {
			margin-bottom: 10px;
		}
	}
	&__button {
		margin-top: 20px;
	}
}
</style>
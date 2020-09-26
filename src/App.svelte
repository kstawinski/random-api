<script>
import Card from './components/Card.svelte';
import Button from './components/Button.svelte';
import About from './components/About.svelte';
import axios from 'axios';

const _API = 'https://api.publicapis.org';

const state = {
	showAPI: false,
	randomAPILoading: false,
};

let fetchedAPI = {};

const getRandomAPI = () => {
	state.randomAPILoading = true;

	axios.get(`${_API}/random?auth=null`)
		.then((answer) => {
			// handle success
			const response = answer.data.entries[0];

			// save response to API object
			fetchedAPI = response;

			// show card
			state.showAPI = true;

			// stop buttons loading
			state.randomAPILoading = false;
		})
		.catch((error) => {
			// handle error
			console.log(error);
		});
};
</script>

<main class="home">
	<div class="container container__flex">
		<section class="home__sidebar sidebar">
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
			<Button text="Search" />
			<Button
				text="Randomize API"
				type="secondary"
				on:click={getRandomAPI}
				loading={state.randomAPILoading}
			/>
		</section>
		<div class="home__content">
			{#if state.showAPI}
				 <Card data={fetchedAPI} />
			{:else}
				 <About />
			{/if}
		</div>
	</div>
</main>

<style type="text/scss">
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500&display=swap');

.home {
	display: flex;
	width: 100vw;
	height: 100vh;
	margin: 0 auto;
	align-items: center;
	justify-content: center;

	&__sidebar {
		width: 30%;
	}
	&__content {
		width: 60%;
	}
}

.container {
	width: 60%;
	margin: 0 auto;

	&__flex {
		display: flex;
		justify-content: space-between;
	}
}

.sidebar {
	box-shadow: 0 10px 10px #ececec;
	padding: 25px;

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
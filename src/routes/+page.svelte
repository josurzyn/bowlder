<script>
	import Header from '$lib/Header.svelte';
	import {
		cookedVegetables,
		dressings,
		fruits,
		grains,
		herbsAndSpices,
		nutsAndSeeds,
		proteins,
		rawVegetables,
		saladGreens,
		welcomeMessages
	} from '../stuff';
	import Bowl from '../lib/Bowl.svelte';

	let showBowl = false;
	let showInfo = false;

	let bowl = [getRandomItem(welcomeMessages)];

	/**
	 *
	 * @param ingredients {string[]}
	 * @param number {number}
	 */
	function getRandomItems(ingredients, number) {
		const shuffled = [...ingredients].sort(() => 0.5 - Math.random());
		return shuffled.slice(0, number);
	}

	/**
	 *
	 * @param items {string[]}
	 */
	function getRandomItem(items) {
		return items[Math.floor(Math.random() * items.length)];
	}

	function createBowl() {
		showInfo = false;
		showBowl = true;
		const grain = getRandomItem(grains);
		const protein = getRandomItem(proteins);
		const cookedVeg = getRandomItem(cookedVegetables);
		const rawVeg = getRandomItems(rawVegetables, 2);
		const fruit = Math.random() > 0.5 ? getRandomItem(fruits) : '';
		const nut = getRandomItem(nutsAndSeeds);
		const dressing = getRandomItem(dressings);
		const herb = getRandomItem(herbsAndSpices);
		const salad = getRandomItem(saladGreens);

		bowl = [grain, protein, cookedVeg, ...rawVeg, fruit, salad, nut, dressing, herb].filter(
			Boolean
		);
	}

	function toggleInfo() {
		showInfo = !showInfo;
	}

	function reset() {
		showBowl = false;
		showInfo = false;

		bowl = [getRandomItem(welcomeMessages)];
	}
</script>

<Header {showBowl} {showInfo} on:reset={reset} on:toggleInfo={toggleInfo} />

<section class="home" class:show-bowl={showBowl}>
	<Bowl {bowl} {showBowl} />

	<button on:click={createBowl} class="build-btn"
		>{#if !showBowl}build your bowl &#9654{:else}new bowls please!{/if}</button
	>
</section>

<style>
	.home {
		display: flex;
		flex-direction: column;
		justify-content: center;
		height: 92%;
		transition: background-color 500ms ease-in-out;
	}
	.home.show-bowl {
		background-color: #000;
	}
	.build-btn {
		margin: auto;
		background-color: #faab20;
		padding: 0.75rem 1.5rem;
		border-radius: 2rem;
		border: none;
		font-size: 1.1rem;
	}
</style>

<script>
	import { createEventDispatcher } from 'svelte';
	import Info from './Info.svelte';

	export let showBowl = false;

	const dispatch = createEventDispatcher();

	/** @type boolean  */
	export let showInfo = false;

	function toggleInfo() {
		dispatch('toggleInfo');
	}

	function reset() {
		dispatch('reset');
	}
</script>

<header class="header" class:bowl={showBowl}>
	<h2 on:click={reset} class="title">bowlder</h2>
	{#if !showInfo}
		<button on:click={toggleInfo} class="info" class:bowl={showBowl}>i</button>
	{:else}
		<button on:click={toggleInfo} class="info" class:bowl={showBowl}>𝗫</button>
	{/if}
</header>

{#if showInfo}
	<Info />
{/if}

<style>
	.header {
		display: flex;
		align-items: center;
		justify-content: flex-end;
		padding-right: 2rem;
		gap: 1rem;
		height: 8%;
		transition: background-color 500ms ease-in-out;
	}
	.header.bowl {
		background-color: #000;
	}
	.title {
		color: #faab20;
		margin: 0 0.5rem;
		cursor: pointer;
	}
	.info {
		border: none;
		border-radius: 50%;
		height: 2rem;
		width: 2rem;
		display: flex;
		align-items: center;
		justify-content: center;
		background-color: #000;
		color: #faab20;
		cursor: pointer;
		font-weight: 800;
		transition: background-color 500ms ease-in-out;
	}
	.info.bowl {
		background-color: #faab20;
		color: #000;
	}
</style>

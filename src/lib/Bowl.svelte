<script>
	import { fade } from 'svelte/transition';

	export let showBowl = false;

	/** @type string[] */
	export let bowl = [];
</script>

<div class="bowl" class:show-bowl={showBowl}>
	{#key bowl.join('')}
		<ul in:fade={{ duration: 400, delay: 200 }} class="bowl-list">
			{#each bowl as item}
				{#key item}
					<li class="bowl-list-item" class:show-bowl={showBowl} out:fade={{ duration: 200 }}>
						{item}
					</li>
				{/key}
			{/each}
		</ul>
	{/key}
</div>

<style>
	.bowl {
		margin: 5rem auto;
		background-color: #000;
		border-radius: 50%;
		height: 80vw;
		max-height: 30rem;
		width: 80vw;
		max-width: 30rem;
		display: flex;
		align-items: center;
		justify-content: center;
		transition: background-color 500ms ease-in-out;
	}
	.bowl.show-bowl {
		background-color: #fff;
	}
	.bowl-list {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		max-width: 25rem;
		padding: 0;
		position: absolute;
	}
	.bowl-list-item.show-bowl {
		color: #000;
		font-size: 2rem;
		line-height: unset;
		white-space: nowrap;
	}
	.bowl-list-item {
		list-style: none;
		color: #faab20;
		font-size: 6.2rem;
		text-align: center;
		line-height: 5rem;
		font-family: 'Bebas Neue', sans-serif;
	}

	@media screen and (max-width: 34rem) {
		.bowl-list-item {
			font-size: 2rem;
		}
		.bowl-list-item.show-bowl {
			font-size: 1.5rem;
		}
	}
</style>

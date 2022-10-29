<script>
	import { scale } from 'svelte/transition';
</script>

<section transition:scale class="info-section">
	<h2>Welcome to bowlder</h2>
	<p>Fancy a bowl but don't know what to put in it? No worries! we’ll take care of that for you.</p>
	<p>
		bolwder randomly picks ingredients from a number of categories like grains, veg, fruit,
		protein... and adds a few little extras to keep things interesting, so you can have a quick,
		healthy dinner with as little planning as possible.
	</p>
	<p>made with ❤ by Celina and Jo</p>
</section>

<style>
	.info-section {
		position: absolute;
		right: 0;
		left: 0;
		margin: 3rem auto;
		border-radius: 50%;
		height: 70vw;
		width: 70vw;
		max-height: 30rem;
		max-width: 30rem;
		background-color: #d9d9d9;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		padding: 3rem;
		z-index: 1;
	}

	@media screen and (max-width: 34rem) {
		.info-section {
			font-size: small;
		}
	}
</style>

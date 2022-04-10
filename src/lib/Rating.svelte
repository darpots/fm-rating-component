<script>
	export let active;
</script>

<div class="rating" class:active on:click>
	<slot />
</div>

<style>
	.rating {
		background-color: var(--darkBlue);
		font-weight: 700;
		font-size: 16px;
		text-align: center;
		color: var(--mediumGrey);
		border-radius: 50%;
		width: 51px;
		height: 51px;
		display: grid;
		place-content: center;
	}
	.rating:hover {
		background-color: var(--mediumGrey);
		color: var(--white);
		transition: all 0.2s ease-in-out;
	}
	.rating.active {
		background-color: var(--orange);
		color: var(--white);
	}

	@media screen and (max-width: 375px) {
		.rating {
			width: 42px;
			height: 42px;
		}
	}
</style>

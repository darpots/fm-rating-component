<script>
	import '$lib/globalStyles.css';

	import Rating from '$lib/Rating.svelte';

	let num_ratings = 5;
	$: ratings = Array.from(Array(num_ratings).keys());

	let currentRating; // default = undefined
	let notSubmitted = true; // default = true
</script>

<svelte:head>
	<title>Interactive Rating Component</title>
</svelte:head>

<main class="card">
	{#if notSubmitted}
		<div class="question">
			<div class="star-background">
				<img src="/icon-star.svg" alt="star" />
			</div>

			<h1>How did we do?</h1>
			<p>
				Please let us know how we did with your support request. All feedback is appreciated to help
				us improve our offering!
			</p>

			<div class="ratings-block">
				{#each ratings as rating}
					<Rating
						on:click={() => (currentRating = rating + 1)}
						active={currentRating === rating + 1}
					>
						{rating + 1}
					</Rating>
				{/each}
			</div>

			<button on:click={() => (notSubmitted = false)}>Submit</button>
		</div>
	{:else}
		<div class="thank-you">
			<div class="thank-you-image">
				<img src="illustration-thank-you.svg" alt="thank you" />
			</div>
			<div class="score">You selected {currentRating} out of {num_ratings}</div>
			<h1>Thank you</h1>
			<p>
				We appreciate you taking the time to give a rating. If you ever need more support, don’t
				hesitate to get in touch!
			</p>
		</div>
	{/if}
</main>

<style>
	.card {
		width: 25.75rem;
		background: radial-gradient(98.96% 98.96% at 50% 0%, #232a34 0%, #181e27 100%);
		border-radius: 1.875rem;
		padding: 2rem;
	}

	.star-background {
		width: 3rem;
		height: 3rem;
		background-color: var(--darkBlue);
		border-radius: 50%;
		display: grid;
		place-content: center;
		margin-bottom: 1.875rem;
	}

	h1 {
		margin-bottom: 0.4375rem;
	}

	p {
		line-height: 1.5rem;
		margin-bottom: 1.5rem;
		max-width: 21.25rem;
	}

	button {
		font-size: 0.9375rem;
		font-weight: 700;
		text-transform: uppercase;
		color: var(--white);
		border: 0;
		border-radius: 1.4063rem;
		line-height: 1.1875rem;
		letter-spacing: 2px;
		padding: 0.6875rem 0;
		background: var(--orange);
		width: 100%;
	}
	button:hover {
		background-color: var(--white);
		color: var(--orange);
		transition: all 0.2s ease-in-out;
	}

	.ratings-block {
		display: flex;
		justify-content: space-between;
		margin-bottom: 2rem;
	}

	.thank-you {
		text-align: center;
	}

	.thank-you-image {
		margin-bottom: 2rem;
	}

	.score {
		background: var(--darkBlue);
		display: inline-block;
		padding: 0.25rem 1.25rem;
		border-radius: 1.4063rem;
		color: var(--orange);
		margin-bottom: 2rem;
	}

	@media screen and (max-width: 23.4375rem) {
		.card {
			padding: 1.5rem 1.5rem 2rem 1.5rem;
			width: 20.4375rem;
		}

		.star-background {
			width: 2.5rem;
			height: 2.5rem;
			margin-bottom: 1rem;
		}

		h1,
		p,
		.ratings-block,
		.thank-you-image,
		.score {
			margin-bottom: 1.5rem;
		}
	}
</style>

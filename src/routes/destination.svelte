<script>
	import Background from '$lib/Background.svelte';
	import { destinations } from '$lib/data.json';
	import PageTitle from '$lib/PageTitle.svelte';
	import SliderListener from '$lib/SliderListener.svelte';
	import { fade } from 'svelte/transition';

	let index = 0;
</script>

<SliderListener bind:index maxIndex={destinations.length} />
<Background />
<PageTitle number="01" title="Pick your destination" />

<div class="contentHolder">
	<div class="destinationTabs subheading2">
		<button class:currentDestination={index === 0} on:click={() => (index = 0)}>Moon</button>
		<button class:currentDestination={index === 1} on:click={() => (index = 1)}>Mars</button>
		<button class:currentDestination={index === 2} on:click={() => (index = 2)}>Europa</button>
		<button class:currentDestination={index === 3} on:click={() => (index = 3)}>Titan</button>
	</div>
	{#each [destinations[index]] as destination (index)}
		<div class="textContainer" transition:fade|local>
			<h2 class="name heading2">{destination.name}</h2>
			<p class="description">{destination.description}</p>
			<div class="statsHolder">
				<div class="statItem">
					<div class="subheading2">Avg. Distance</div>
					<div class="subheading1">{destination.distance}</div>
				</div>
				<div class="statItem">
					<div class="subheading2">Est. Travel Time</div>
					<div class="subheading1">{destination.travel}</div>
				</div>
			</div>
		</div>
		<picture class="image" transition:fade|local>
			<source srcset={destination.images.webp} type="image/webp" />
			<source srcset={destination.images.png} type="image/jpeg" />
			<img src={destination.images.png} alt="Destination" />
		</picture>
	{/each}
</div>

<style>
	.contentHolder {
		display: grid;
		grid-template-areas:
			'image'
			'slider'
			'text';
	}
	.image {
		grid-area: image;
		margin-top: 2rem;
	}
	img {
		height: 170px;
		width: 170px;
	}
	.destinationTabs {
		margin: 1.5rem auto;
		grid-area: slider;
		display: flex;
		gap: 1rem;
	}
	button {
		cursor: pointer;
		text-transform: uppercase;
		padding-bottom: 0.5rem;
		background: none;
		border: none;
		color: rgb(var(--color-mid));
		border-bottom: 3px solid transparent;
	}
	button:hover:not(.currentDestination) {
		border-color: rgba(var(--color-light), 0.5);
	}
	.currentDestination {
		border-color: rgb(var(--color-light));
	}
	.textContainer {
		margin: auto;
		grid-area: text;
		width: 327px;
	}
	.statsHolder {
		margin-top: 2rem;
		border-top: 1px solid rgb(var(--color-mid));
		grid-area: stats;
		grid-template-columns: 1fr;
		display: flex;
		flex-direction: column;
		justify-content: space-around;
	}
	.statItem {
		margin-top: 2rem;
		display: flex;
		flex-direction: column;
		gap: 0.75rem;
	}
	.subheading2 {
		color: rgb(var(--color-mid));
	}
	.subheading1 {
		padding: 0;
		margin-top: 0;
	}

	@media screen and (min-width: 641px) {
		.textContainer {
			width: 573px;
		}
		img {
			height: 300px;
			width: 300px;
		}
		.statsHolder {
			margin-top: 3rem;
			flex-direction: row;
		}
	}

	@media screen and (min-width: 1008px) {
		.subheading1,
		.subheading2 {
			text-align: start;
		}

		.image {
			margin: auto;
		}
		img {
			margin: auto;
			height: 445px;
			width: 445px;
			padding: 2rem;
		}

		.contentHolder {
			margin-left: 10rem;
			grid-template-columns: 1fr 1fr;
			justify-items: space-between;
			grid-template-areas:
				'image slider'
				'image text';
		}

		.destinationTabs {
			margin: 0;
			gap: 2rem;
		}

		.textContainer {
			margin: 0;
			width: 100%;
			max-width: 445px;
		}
		.statsHolder {
			display: grid;
			grid-template-columns: 1fr 1fr;
			justify-items: flex-start;
		}
	}
</style>

<script>
	import Background from '$lib/Background.svelte';
	import { technology } from '$lib/data.json';
	import PageTitle from '$lib/PageTitle.svelte';
	import SliderListener from '$lib/SliderListener.svelte';
	import { fade } from 'svelte/transition';

	let index = 0;
	// $: item = technology[index];
</script>

<SliderListener bind:index maxIndex={technology.length} />
<Background slot="background" />
<PageTitle number="03" title="space launch 101" />
<div class="contentHolder">
	<div class="slider">
		<button on:click={() => (index = 0)} class:current={index === 0}>1</button>
		<button on:click={() => (index = 1)} class:current={index === 1}>2</button>
		<button on:click={() => (index = 2)} class:current={index === 2}>3</button>
	</div>
	{#each [technology[index]] as item (index)}
		<div class="textContainer" transition:fade|local>
			<div class="title_text">the terminology...</div>
			<h2 class="heading3">{item.name}</h2>
			<p>{item.description}</p>
		</div>
		<picture class="image" transition:fade|local>
			<source media="(max-width:1007px)" srcset={item.images.landscape} type="image/jpeg" />
			<img src={item.images.portrait} alt="Technology Item" />
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
	.slider {
		margin: auto;
		margin-bottom: 1.6rem;
		display: flex;
		gap: 1rem;
		grid-area: slider;
	}
	picture {
		grid-area: image;
	}
	img {
		width: 100vw;
		margin: 2rem auto;
	}
	.textContainer {
		grid-area: text;
	}
	.title_text {
		color: rgb(var(--color-mid));
		font-size: 0.8rem;
		font-family: 'Barlow Condensed', sans-serif;
		font-weight: normal;
		text-transform: uppercase;
		letter-spacing: 0.169rem;
		margin-bottom: 0.5rem;
	}

	p {
		max-width: 327px;
		padding-top: 1rem;
		margin: auto;
	}
	button {
		font-family: 'Bellefair', serif;
		background-color: transparent;
		height: 40px;
		width: 40px;
		color: rgb(var(--color-light));
		border: 1px solid rgb(var(--color-light));
		border-radius: 50%;
	}

	.current {
		color: rgb(var(--color-dark));
		background-color: rgb(var(--color-light));
	}

	@media screen and (min-width: 1008px) {
		.contentHolder {
			margin-left: 10rem;
			column-gap: 5rem;
			grid-template-columns: auto 1fr auto;
			grid-template-areas: 'slider text image';
			align-items: center;
		}
		.textContainer {
			align-self: flex-start;
			margin-top: 9rem;
		}
		button {
			height: 80px;
			width: 80px;
			font-size: 2rem;
		}
		p {
			margin: 0;
			max-width: 445px;
		}
		.slider {
			margin: 0;
			flex-direction: column;
		}
		img {
			justify-self: end;
			width: auto;
		}
	}
</style>

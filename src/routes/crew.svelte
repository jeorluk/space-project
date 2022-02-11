<script>
	import Background from '$lib/Background.svelte';
	import { crew } from '$lib/data.json';
	import PageTitle from '$lib/PageTitle.svelte';
	import SliderListener from '$lib/SliderListener.svelte';
	import { fade, fly } from 'svelte/transition';

	let index = 0;
	$: console.log(index);
</script>

<SliderListener bind:index maxIndex={crew.length} />
<Background />
<div class="contentHolder">
	<div class="title">
		<PageTitle number="02" title="meet your crew" />
	</div>
	<div class="slider">
		<button class="node" class:currentMember={index === 0} on:click={() => (index = 0)} />
		<button class="node" class:currentMember={index === 1} on:click={() => (index = 1)} />
		<button class="node" class:currentMember={index === 2} on:click={() => (index = 2)} />
		<button class="node" class:currentMember={index === 3} on:click={() => (index = 3)} />
	</div>
	{#each [crew[index]] as member (index)}
		<picture class="image" transition:fade|local>
			<source srcset={member.images.webp} type="image/webp" />
			<source srcset={member.images.png} type="image/jpeg" />
			<img src={member.images.png} alt="Crew member" />
		</picture>
		<div class="textContainer" transition:fade|local>
			<div class="heading4">{member.role}</div>
			<h2 class="heading3">{member.name}</h2>
			<p>{member.bio}</p>
		</div>
	{/each}
</div>

<style>
	.contentHolder {
		padding: 0 1.5rem;
		display: grid;
		row-gap: 1.5rem;
		justify-items: center;
		grid-template-areas:
			'title'
			'image'
			'slider'
			'text';
	}
	.slider {
		grid-area: slider;
		list-style: none;
		display: flex;
	}
	.node {
		background: transparent;
		border: none;
		display: grid;
		place-items: center;
		height: 35px;
		width: 35px;
	}

	.node::after {
		content: '';
		position: relative;
		z-index: -1;
		top: 0;
		right: 0;
		height: 10px;
		width: 10px;
		border-radius: 50%;
		background-color: rgba(var(--color-light), 0.25);
	}
	.node:not(.currentMember):hover:after {
		background-color: rgba(var(--color-light), 0.5);
	}
	.currentMember::after {
		background-color: rgb(var(--color-light));
	}

	.title {
		grid-area: title;
	}

	.image {
		border-bottom: 1px solid rgba(var(--color-light), 0.4);
		height: 250px;
		width: 100%;
		margin: auto;
		grid-area: image;
	}

	img {
		max-height: 100%;
		max-width: 100%;
	}

	.textContainer {
		height: 100%;
		grid-area: text;
		max-width: 330px;
	}

	.heading4 {
		padding: 0;
		margin: 0;
		color: rgba(var(--color-light), 0.4);
	}

	@media screen and (min-width: 641px) {
		.contentHolder {
			grid-template-areas:
				'title'
				'text'
				'slider'
				'image';
		}
		.image {
			height: 572px;
		}
		.title {
			justify-self: flex-start;
		}
		.textContainer {
			max-width: 465px;
		}
	}
	@media screen and (min-width: 1008px) {
		.contentHolder {
			padding-left: 10rem;
			height: 100%;
			grid-template-columns: 2fr minmax(0, 2fr);
			grid-template-rows: auto 1fr auto;
			grid-template-areas:
				'title image'
				'text image'
				'slider image';
			justify-items: flex-start;
		}
		.image {
			height: 100%;
			display: flex;
			justify-content: flex-start;
			width: 100%;
			max-width: 500px;
			border-bottom: none;
		}
		img {
			align-self: flex-end;
			height: auto;
			max-width: 100%;
		}

		.title :global(h1) {
			padding: 0;
		}
		.textContainer {
			padding-top: 2rem;
			max-width: 100%;
		}

		p {
			padding-top: 2rem;
			max-width: 440px;
		}
		.slider {
			padding-bottom: 5rem;
		}
	}
</style>

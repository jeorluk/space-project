<script>
	import Background from '$lib/Background.svelte';
	import ExploreButton from '$lib/ExploreButton.svelte';
</script>

<Background />
<div class="content">
	<div class="textContainer">
		<div class="heading5">So, you want to travel to</div>
		<h1 class="heading1">Space</h1>
		<p>
			Let’s face it; if you want to go to space, you might as well genuinely go to outer space and
			not hover kind of on the edge of it. Well sit back, and relax because we’ll give you a truly
			out of this world experience!
		</p>
	</div>
	<div class="buttonContainer">
		<ExploreButton />
	</div>
</div>

<style>
	.content {
		display: grid;
		grid-template-rows: 2fr 1fr;
		grid-template-areas:
			'text'
			'button';
	}
	.textContainer {
		grid-area: text;
		margin: 0 auto;
	}
	.buttonContainer {
		grid-area: button;
	}

	@media screen and (max-width: 640px) {
		.textContainer {
			max-width: 330px;
			margin-top: 3.6rem;
		}
	}

	@media screen and (min-width: 641px) {
		.content {
			max-height: 100%;
			align-items: flex-end;
			grid-template-rows: 1fr;
			grid-template-areas: 'text button';
		}
		.heading1 {
			padding: 0;
			margin: 3rem 0;
		}
		.textContainer {
			max-width: 450px;
			margin-top: 6.5rem;
		}
		p {
			max-width: 27.75rem;
			margin: auto;
		}
	}

	@media screen and (min-width: 1008px) {
		.textContainer {
			width: 450px;
		}

		h1 {
			text-align: left;
			padding: 2rem 0;
		}
		p {
			margin: 0;
		}
	}
</style>

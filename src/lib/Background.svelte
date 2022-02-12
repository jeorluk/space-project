<script>
	import { page } from '$app/stores';
</script>

{#if $page.url.pathname === '/'}
	<picture>
		<source media="(max-width: 640px)" srcset="/home/background-home-mobile.jpg" />
		<source media="(max-width: 1007px)" srcset="/home/background-home-tablet.jpg" />
		<img src="/home/background-home-desktop.jpg" alt="Background" />
	</picture>
{:else if $page.url.pathname === '/crew'}
	<picture>
		<source media="(max-width: 640px)" srcset="/crew/background-crew-mobile.jpg" />
		<source media="(max-width: 1007px)" srcset="/crew/background-crew-tablet.jpg" />
		<img src="/crew/background-crew-desktop.jpg" alt="Background" />
	</picture>
{:else if $page.url.pathname === '/destination'}
	<picture>
		<source media="(max-width: 640px)" srcset="/destination/background-destination-mobile.jpg" />
		<source media="(max-width: 1007px)" srcset="/destination/background-destination-tablet.jpg" />
		<img src="/destination/background-destination-desktop.jpg" alt="Background" />
	</picture>
{:else if $page.url.pathname === '/technology'}
	<picture>
		<source media="(max-width: 640px)" srcset="/technology/background-technology-mobile.jpg" />
		<source media="(max-width: 1007px)" srcset="/technology/background-technology-tablet.jpg" />
		<img src="/technology/background-technology-desktop.jpg" alt="Background" />
	</picture>
{/if}

<style>
	picture {
		padding: 0;
		margin: 0;
		display: flex;
		min-height: 100vh;
		width: 100%;
		position: absolute;
		top: 0;
		left: 0;

		z-index: -1;
	}

	picture img {
		object-fit: cover;
		object-position: top;
		height: 100%;
		width: 100%;
	}

	@media screen and (min-width: 1008px) {
		picture {
			height: 100vh;
		}
	}
</style>

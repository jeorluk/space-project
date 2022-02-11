<script>
	import { page } from '$app/stores';

	let isMenuOpen = false;
</script>

<button class="menuToggle" class:active={isMenuOpen} on:click={() => (isMenuOpen = !isMenuOpen)} />

<nav class:open={isMenuOpen}>
	<ul class="menu container">
		<li class:current={$page.path === '/'}>
			<a on:click={() => (isMenuOpen = !isMenuOpen)} href="/"
				><strong class="number">00</strong> Home</a
			>
		</li>
		<li class:current={$page.path === '/destination'}>
			<a on:click={() => (isMenuOpen = !isMenuOpen)} href="/destination"
				><strong class="number">01</strong> Destination</a
			>
		</li>
		<li class:current={$page.path === '/crew'}>
			<a on:click={() => (isMenuOpen = !isMenuOpen)} href="/crew"
				><strong class="number">02</strong> Crew</a
			>
		</li>
		<li class:current={$page.path === '/technology'}>
			<a on:click={() => (isMenuOpen = !isMenuOpen)} href="/technology"
				><strong class="number">03</strong> Technology</a
			>
		</li>
	</ul>
</nav>

<style>
	ul {
		text-transform: uppercase;
		list-style: none;
		text-decoration: none;
		display: flex;
		background-color: rgba(var(--color-light), 0.04);
		backdrop-filter: blur(20px);
	}
	a,
	a:visited {
		display: block;
		color: inherit;
		text-decoration: none;
	}
	@media screen and (max-width: 640px) {
		nav {
			overflow: hidden;
			display: none;
			position: absolute;
			top: 0;
			right: -65vw;
			height: 100vh;
			width: 65vw;
			transition: ease-in 0.2s;
		}

		.open {
			display: block;
			transform: translateX(-65vw);
		}

		ul {
			height: 100%;
			width: 100%;
			padding: 2rem;
			padding-top: 7.5rem;
			flex-direction: column;
			row-gap: 2rem;
			font-family: 'Barlow Condensed', sans-serif;
			font-weight: normal;
			text-transform: uppercase;
			letter-spacing: 0.169rem;
		}

		button {
			position: absolute;
			top: 0;
			right: 0;
			z-index: 100;

			margin: 2rem;
			height: 1.5rem;
			width: 1.5rem;

			background-color: transparent;
			background-image: url('/shared/icon-hamburger.svg');
			background-size: 100% 100%;
			border: none;
		}
		.active {
			background-image: url('/shared/icon-close.svg');
		}
	}
	@media screen and (min-width: 641px) {
		.number {
			display: none;
		}
		button {
			display: none;
		}
		nav {
			display: block;
		}
		ul {
			display: flex;
			gap: 2rem;
			padding: 0 4rem;
		}
		li {
			display: inline-block;
			border-bottom: 3px solid transparent;
		}

		li:hover:not(.current) {
			border-bottom: 3px solid rgba(var(--color-light), 0.5);
		}
		a {
			line-height: 6rem;
		}
		.current {
			border-bottom: 3px solid rgb(var(--color-light));
		}
	}
	@media screen and (min-width: 1008px) {
		.number {
			display: inline-block;
			padding-right: 0.5rem;
		}
		ul {
			padding-left: 8rem;
			padding-right: 10rem;
		}
	}
</style>

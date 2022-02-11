<script>
	import '../app.css';
	import NavBar from '$lib/NavBar.svelte';
</script>

<head>
	<meta charset="UTF-8" />
	<meta name="viewport" content="width=device-width, initial-scale=1.0" />

	<link rel="icon" type="image/png" sizes="32x32" href="/static/favicon-32x32.png" />

	<title>Frontend Mentor | Space tourism website</title>
</head>

<div class="page">
	<header>
		<img class="logo" src="/shared/logo.svg" alt="Space Logo" />
		<NavBar />
	</header>
	<main>
		<slot />
	</main>
</div>

<style>
	.page {
		min-height: 100vh;
		display: grid;
		grid-template-rows: auto 1fr;
	}
	header {
		width: 100%;
		display: flex;
	}
	main {
		text-align: center;
	}

	@media screen and (max-width: 640px) {
		header {
			padding: 1.5rem;
		}
		.logo {
			height: 40px;
			width: 40px;
		}
	}

	@media screen and (min-width: 641px) {
		header {
			justify-content: space-between;
		}
		.logo {
			margin-top: 1.5rem;
			margin-left: 2rem;
			height: 3rem;
			width: 3rem;
		}
	}

	@media screen and (min-width: 1008px) {
		header {
			padding-top: 2.5rem;
		}
		main {
			text-align: initial;
		}
	}
</style>

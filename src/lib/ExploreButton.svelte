<a href="/destination">Explore</a>

<style>
	a {
		display: grid;
		place-items: center;
		height: 150px;
		width: 150px;
		margin: auto;
		border-radius: 50%;

		font-family: 'Bellefair', serif;
		font-size: 1.25rem;
		letter-spacing: 0.078;
		text-transform: uppercase;
		text-decoration: none;

		color: rgb(var(--color-dark));
		background-color: rgb(var(--color-light));
		transition: box-shadow 0.3s;
	}

	a:hover {
		box-shadow: 0 0 0 3rem rgb(var(--color-light), 0.11);
	}

	@media screen and (min-width: 641px) {
		a {
			height: 242px;
			width: 242px;
			font-size: 2rem;
			margin: 0 auto;
		}
	}
	@media screen and (min-width: 1008px) {
		a {
			height: 274px;
			width: 274px;
			font-size: 2rem;
			margin: 0 auto;
		}
	}
</style>

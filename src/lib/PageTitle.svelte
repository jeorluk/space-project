<script>
	export let number = '';
	export let title = '';
</script>

<h1 class="heading5 light pageTitle"><span class="light_dim">{number}</span>{title}</h1>

<style>
	span {
		padding-right: 1rem;
	}
	@media screen and (min-width: 641px) {
		.pageTitle {
			margin-top: 2.5rem;
			text-align: start;
			padding-left: 2.5rem;
		}
	}

	@media screen and (min-width: 1008px) {
		.pageTitle {
			margin-top: 4.75rem;
			text-align: start;
			padding-left: 10.5rem;
		}
	}
</style>

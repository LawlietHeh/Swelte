<script lang="ts">
	import Header from "./Header.svelte";
	import "../app.css";
	import Counter from "./Counter.svelte";
	import produkt from "./Produkt.svelte";
	import Produkt from "./Produkt.svelte";
	import Kartazakupowa from "./kartazakupowa.svelte";
	import Koncowka from "./koncowka.svelte";
	let { children } = $props();
</script>

<div class="app">
	<!-- <Header /> -->
	<main>
		{@render children()}
		<div>s</div>
		<!-- <Counter startingamount={3} /> -->
		<!-- 
		<Kartazakupowa />
		<hr />
		<Produkt idProduktu={1} />
		<hr />
		<Produkt idProduktu={2} />
		<hr />
		<Produkt />
		<hr />
		<Produkt />
		<Koncowka /> -->

		<!-- <footer>
		<p>
			visit <a href="https://svelte.dev/docs/kit">svelte.dev/docs/kit</a> to
			learn about SvelteKit
		</p>
	</footer> -->
	</main>
	
</div>

<style>
	.app {
		display: flex;
		flex-direction: column;
		min-height: 100vh;
	}

	button {
		width: 300px;
		background-color: red;
	}
	main {
		flex: 1;
		display: flex;
		flex-direction: column;
		padding: 1rem;
		width: 100%;
		max-width: 64rem;
		margin: 0 auto;
		box-sizing: border-box;
	}

	footer {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		padding: 12px;
	}

	footer a {
		font-weight: bold;
	}

	@media (min-width: 480px) {
		footer {
			padding: 12px 0;
		}
	}
	hr {
		width: 80.6%;
	}
	div {
		background-size: 100% 10%;
		background-image: url(#);
	}
</style>

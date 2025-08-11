<script lang="ts">
	let { startingamount } = $props();
	let licznik = $state(startingamount);
</script>

{licznik}
<button onclick={() => licznik++}>+</button><br />
<button onclick={() => licznik--}>-</button>

<style>
	button {
		width: 300px;
		background-color: red;
	}
</style>

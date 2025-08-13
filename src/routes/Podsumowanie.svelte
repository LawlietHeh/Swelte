<script lang="ts">
    import type { Product, Totals } from "./+page.svelte";
    type Props = {
        totals: Map<Product["id"], Totals>;
    };

    let { totals }: Props = $props();
    function oneclick() {
        console.log(totals);
    }

    let suma = $derived(
        Array.from(totals.values()).reduce((acc, val) => acc + val.total, 0),
    );
</script>

<div>
    <br />
    <p id="podsumowanie">&nbsp;&nbsp;Podsumowanie:<br />{suma}</p>
    <button on:click={oneclick}>s</button>
    <hr />
    {totals.size}
    <br />
</div>

<style>
    div {
        background-color: rgba(255, 255, 255, 0.445);
        height: 700px;
        width: 300px;
        position: fixed;
        top: 130px;
        right: 0%;
        border-top-left-radius: 20px;
        border-bottom-left-radius: 20px;
        padding: 20px;
        justify-content: center;
    }

    #podsumowanie {
        font-size: 27px;
        justify-content: center;
    }
</style>

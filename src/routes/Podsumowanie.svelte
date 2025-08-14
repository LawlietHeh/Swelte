<script lang="ts">
    import type { Product, Totals } from "./+page.svelte";
    type Props = {
        totals: Map<Product["id"], Totals>;
    };
    let cenaPoPromocji: number = $state(0);
    let rabat: number = 5000;
    let { totals }: Props = $props();
    function oneclick() {
        console.log(totals);
    }
    let suma = $derived(
        Array.from(totals.values()).reduce((acc, val) => acc + val.total, 0),
    );
    let sumaIlosci = $derived(
        Array.from(totals.values()).reduce((acc, val) => acc + val.count, 0),
    );
    console.log(suma, rabat);
    let kolorSuma = "black";
    let linia = "none";
    $effect(() => {
        if (suma >= rabat) {
            cenaPoPromocji = suma * 0.9;
            kolorSuma = "red";
            linia = "line-through";
        } else {
            cenaPoPromocji = suma;
            kolorSuma = "black";
            linia = "none";
        }
    });
</script>

<div>
    <br />
    <p id="podsumowanie">Podsumowanie:<br /></p>
    <hr />
    <p style="color:  {kolorSuma}; text-decoration: {linia}">
        {suma.toFixed(2)}
    </p>
    {#if suma >= rabat}
        <p id="rabat">{cenaPoPromocji.toFixed(2)}</p>
    {/if}
    <hr />
    <p id="podsumowanie">Sztuki:</p>
    <p>{sumaIlosci}</p>

    <br />
</div>

<style>
    p {
        text-align: center;
        font-size: 25px;
    }
    div {
        background-color: rgba(255, 255, 255, 0.757);
        height: 700px;
        width: 300px;
        position: fixed;
        top: 130px;
        right: 0%;
        border-top-left-radius: 20px;
        border-bottom-left-radius: 20px;
        padding: 20px;
        justify-content: center;
        background-image: url(#);
        border-style: double;
        border-color: hotpink;
        border-width: 5px;
    }

    #podsumowanie {
        font-size: 30px;
        text-align: center;
        font-family: "Pacifico", cursive;
        font-weight: 400;
        font-style: normal;
        color: rgb(255, 142, 160);
    }
    #rabat {
        color: rgb(60, 214, 158);
    }
</style>

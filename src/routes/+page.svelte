<script context="module">
    export type Product = {
        id: number;
        title: string;
        price: number;
        description: string;
        category: string;
        /** to jest obrazek */
        image: string;
        rating: {
            rate: string;
            count: string;
        };
    };
    export type Totals = {
        total: number;
        count: number;
    };
    export type calkowitailosc = {

    }

</script>

<script lang="ts">
    import { SvelteMap as Map } from "svelte/reactivity";
    import Koncowka from "./koncowka.svelte";
    import Produkt from "./Produkt.svelte";
    import Podsumowanie from "./Podsumowanie.svelte";
    let totals = new Map<Product["id"], Totals>();
    let products: Product[] = $state([]);
    let loading = $state(true)
    async function getData() {
        let responce = await fetch("https://fakestoreapi.com/products");
        let data = await responce.json();
        products = data;
        products.forEach((product) => {
            totals.set(product.id, { total: product.price, count: 1 });
        });
    }
    $effect(() => {
        loading = false;
    }
)
    //
    //
    // let hp = 100
    //
    // let pokemon = {
    //     hp: hp,
    //     damage: 24,
    //     zywiol: 'fire'
    // }

    // pokemon.hp

    function oneclick() {
        console.log(totals);
        console.log(products);
    }

    getData();
    /** ta zmienna przechowuje to i to */
</script>
<div id="koszyk">
Koszyk
{#if loading}
    <div class="loading-screen">
        <img src="../src/lib/images/rikka-loading.gif"/></div><br/>
    <div class="loading-screen2">
        <img id="loading" src="../src/lib/images/loading-ring.gif"/>
    </div>
{/if}
</div>
<div>
    <table>
        <tbody>
            <tr
                ><td>Produkt</td><td
                    >Opis</td
                ><td>Cena</td><td>Ilość</td><td>Wartość</td>
            </tr><tr></tr>
        </tbody>
    </table>
    <br />
    {#each products as product}
        <Produkt {product} {totals} /><br />
    {/each}
</div>
<Podsumowanie {totals} />

<style>
    table {
        background-color: rgba(251, 177, 224, 0.275);
        text-align: center;
        border-radius: 15px;
        
    }
    td {
                background-image: url(../lib/images/chmura.gif);
                background-size: 200px 110px;
                height: 300px;
                font-family: "Pacifico", cursive;
                font-weight: 400;
                font-style: normal;
                font-size: 25px;
                color: rgb(255, 146, 164);
    }
    input {
        width: 45%;
        height: 15%;
    }

    td {
        min-width: 200px;
        height: 110px;
    }
    img {
        height: auto;
        width: 200px;
    }
    button {
        height: 20px;
        width: 90px;
        border-radius: 15px;
        line-height: 20px;
        background-color: rgb(255, 255, 255);
    }
    button:hover {
        height: 20px;
        width: 90px;
        border-radius: 15px;
        line-height: 20px;
        background-color: rgb(255, 255, 255);
        border-color: rgb(87, 87, 87);
        border-style: inset;
        border-width: 2px;
    }
    button:active {
        height: 20px;
        width: 90px;
        border-radius: 15px;
        line-height: 20px;
        background-color: rgba(99, 99, 99, 0.473);
        border-color: rgb(87, 87, 87);
        border-style: inset;
        border-width: 2px;
    }
    #koszyk {
        background-color: rgb(255, 255, 255);
        border-radius: 15px;
        height: 130px;
        width: 100%;
        margin-bottom: 20px;
        font-size: 40px;
        background-image: url(#);
        background-size: 100% 130px;
        text-align: center;
        padding-top: 30px;
  font-family: "Pacifico", cursive;
  font-weight: 400;
  font-style: normal;
          border-style: double;
          border-color: hotpink;
          border-width: 5px;

  color: hotpink;
    }
    .loading-screen {
        position: relative;
        top: 400px;
        left:40%
    }
    .loading-screen2 {
        position: relative;
        height: 50px;
        width: 50px;
        left: 470px;
        top: 55px;
    }
</style>

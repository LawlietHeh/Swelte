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
</script>

<script lang="ts">
    import { SvelteMap as Map } from "svelte/reactivity";
    import Koncowka from "./koncowka.svelte";
    import Produkt from "./Produkt.svelte";
    import Podsumowanie from "./Podsumowanie.svelte";
    let totals = new Map<Product["id"], Totals>();
    let products: Product[] = $state([]);

    async function getData() {
        let responce = await fetch("https://fakestoreapi.com/products");
        let data = await responce.json();
        products = data;
        products.forEach((product) => {
            totals.set(product.id, { total: product.price, count: 1 });
        });
        console.log(totals);
    }

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

<div>
    <table>
        <tbody>
            <tr
                ><td>Produkt<button on:click={oneclick}>s</button></td><td
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
        background-color: rgba(255, 255, 255, 0.781);
        width: 80%;
        height: 100px;
        text-align: center;
        border-radius: 15px;
    }
    input {
        width: 45%;
        height: 15%;
    }

    td {
        min-width: 200px;
        height: 100px;
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
</style>

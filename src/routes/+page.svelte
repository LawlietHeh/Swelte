<script lang="ts">
    import Koncowka from "./koncowka.svelte";
    import Produkt from "./Produkt.svelte";
    let products = [];

    async function getData() {
        let responce = await fetch("https://fakestoreapi.com/products");
        let data = await responce.json();
        products = data;
    }

    getData();
</script>

<div>
    <table>
        <tbody>
            <tr
                ><td>Produkt</td><td>Opis</td><td>Cena</td><td>Ilość</td><td
                    >Wartość</td
                >
            </tr><tr></tr>
        </tbody>
    </table>
    <hr />
    {#each products as product}
        <Produkt
            link={product.image}
            opis={product.description}
            title={product.title}
            price="{product.price}$"
        />
        <hr />
    {/each}
    <hr />
</div>

<style>
    table {
        background-color: rgba(255, 255, 255, 0.336);
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

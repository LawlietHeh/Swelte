<script lang="ts">
    import type { Product, Totals } from "./+page.svelte";
    export type Props = {
        product: Product;
        totals: Map<Product["id"], Totals>;
    };
    let { product, totals }: Props = $props();

    let ilosc = $state(1);

    function increment() {
        ilosc += 1;
        totals.set(product.id, total);
    }

    function decrement() {
        if (ilosc > 1) {
            ilosc -= 1;
        }
        totals.set(product.id, { total: total, count: ilosc });
    }

    let total: number = $derived(product.price * ilosc);

    $effect(() => {
        // This effect ensures 'ilosc' is a number and defaults to 1 if it's not a valid number.
        // The '+' prefix on 'ilosc' in the input will automatically coerce the value to a number,
        // but this adds an extra layer of safety.
        ilosc = +ilosc || 1;
    });
</script>

<div>
    <table>
        <tbody>
            <tr>
                <td>
                    <img src={product.image} alt={product.title} />
                    <p>{product.title}</p>
                </td>
                <td><p id="opis">{product.description}</p></td>
                <td><p>{product.price}$</p></td>
                <td>
                    <button onclick={increment}>+</button><br />
                    <input type="number" min="1" bind:value={ilosc} /><br />
                    <button onclick={decrement}>-</button>
                </td>
                <td>
                    <p id="total">{total}</p>
                </td>
            </tr>
        </tbody>
    </table>
</div>

<style>
    table {
        background-color: rgba(255, 255, 255, 0.336);
        width: 80%;
        height: 200px;
        text-align: center;
        border-radius: 15px;
        transition: 1000ms;
    }
    table:hover {
        background-color: rgba(255, 255, 255, 0.548);
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
        padding: 20px;
    }
    img {
        height: auto;
        width: 190px;
        transition: 1000ms;
    }
    img:hover {
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
    #opis {
        font-size: 10px;
        margin: 30px;
        transition: 500ms;
    }
    #opis:hover {
        font-size: 15px;
        margin: 30px;
    }
    #total {
        background-color: rgba(218, 132, 255, 0.219);
        border-style: none;
        border-radius: 15px;
        width: 150px;
        text-align: center;
        padding: 8px;
    }
</style>

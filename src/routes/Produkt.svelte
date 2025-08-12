<script lang="ts">
    export let link: string;
    export let title: string;
    export let price: number;
    export let opis: string;
    export let cena: number;

    let ilosc = 1;

    function increment() {
        ilosc += 1;
    }

    function decrement() {
        if (ilosc > 1) ilosc -= 1;
    }

    $: total = (cena * ilosc).toFixed(2) + "$";
    $: ilosc = +ilosc || 1;
</script>

<div>
    <table>
        <tbody>
            <tr
                ><td
                    ><img src={link} />
                    <p>{title}</p></td
                >
                <td><p id="opis">{opis}</p></td>
                <td><p>{price}</p></td>
                <td
                    ><button onclick={increment}>+</button><br />
                    <input type="number" min="1" bind:value={ilosc} /><br />
                    <button onclick={decrement}>-</button></td
                >
                <td
                    ><input id="total" min="1" bind:value={total} readonly />
                </td></tr
            >
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
    }
</style>

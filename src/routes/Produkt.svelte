<script lang="ts">
    export let link: string;
    export let title: string;
    export let price: number;
    export let opis: string;

    let ilosc = 1;

    function increment() {
        ilosc += 1;
    }

    function decrement() {
        if (ilosc > 1) ilosc -= 1;
    }

    $: total = (price * ilosc).toFixed(2);
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
                <td><p></p></td></tr
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
    #opis {
        font-size: 10px;
        margin: 30px;
    }
</style>

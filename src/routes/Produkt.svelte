<script lang="ts">
    import monitor from "$lib/images/lenovo44.png";
</script>

<div>
    <table>
        <tbody>
            <tr><td>Produkt</td><td>Cena</td><td>Ilość</td><td>Wartość</td></tr>
            <tr
                ><td><img src={monitor} /></td><td>ss</td><td><input /></td><td
                    ><input readonly /></td
                ></tr
            >
        </tbody>
    </table>
</div>

<style>
    table {
        background-color: rgba(255, 255, 255, 0.336);
        width: 80%;
        height: 300px;
    }
    input {
        width: 40%;
    }

    td {
        min-width: 200px;
        height: 100px;
    }
    img {
        height: 200px;
    }
</style>

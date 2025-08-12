<script lang="ts">
    import monitor from "$lib/images/lenovo44.png";
</script>

<div>
    <table>
        <tbody>
            <tr id="nazwyproduktów"
                ><td>Produkt</td><td>Cena</td><td>Ilość</td><td>Wartość</td></tr
            >
        </tbody>
    </table>
</div>

<style>
    #nazwyproduktów {
        color: white;
        text-shadow: 2px 2px black;
    }
    table {
        background-color: rgba(255, 255, 255, 0.336);
        max-width: 80%;
        height: 100px;
        border-top-left-radius: 15px;
        border-top-right-radius: 15px;
        text-align: center;
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

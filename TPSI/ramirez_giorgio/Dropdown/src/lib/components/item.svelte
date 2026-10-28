<script>
    export let value = "";
</script>

<!-- usiamo "on:click" per forwardare l'evento al parent -->
<button class="item-btn" on:click>
    {value}
</button>

<style>
    .item-btn {
        display: block;
        width: 100%;
        padding: 12px 20px;
        text-align: left;
        background: none;
        border: none;
        border-bottom: 1px solid #f0f0f0;
        font-size: 1rem;
        color: #333;
        font-family: Arial, sans-serif;
        cursor: pointer;
        transition: background-color 0.2s ease, padding-left 0.2s ease;
    }

    .item-btn:last-child {
        border-bottom: none;
    }

    .item-btn:hover {
        background-color: #f9f9f9;
        color: #ff0000;
        padding-left: 24px; /* Piccolo effetto estetico extra */
    }
</style>
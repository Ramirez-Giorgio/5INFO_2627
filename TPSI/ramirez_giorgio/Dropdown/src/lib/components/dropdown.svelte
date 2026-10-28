<script>
    // Props generiche in ingresso
    export let title = "Menu";
    export let isOpen = false;
    export let onToggle = () => {};
</script>

<div class="dropdown-wrapper">
    <button class="dropdown-btn" on:click={onToggle}>
        <span class="title">{title}</span>
        <!-- Icona a freccia che ruota quando isOpen è true -->
        <svg class="chevron" class:open={isOpen} viewBox="0 0 24 24" width="24" height="24">
            <path fill="currentColor" d="M7.41 8.59L12 13.17l4.59-4.58L18 10l-6 6-6-6 1.41-1.41z"/>
        </svg>
    </button>
    
    <!-- Renderizza la tendina solo se isOpen è true -->
    {#if isOpen}
        <div class="dropdown-list">
            <!-- Il tag slot inietta i DropdownItem che passiamo dal parent -->
            <slot />
        </div>
    {/if}
</div>

<style>
    .dropdown-wrapper {
        position: relative;
        width: 320px;
        margin-bottom: 25px;
        font-family: Arial, sans-serif;
    }

    .dropdown-btn {
        width: 100%;
        background-color: #ff0000; /* Il rosso esatto dell'esercitazione */
        color: white;
        font-size: 1.25rem;
        font-weight: bold;
        padding: 14px 20px;
        border: none;
        border-radius: 12px;
        cursor: pointer;
        display: flex;
        justify-content: center;
        align-items: center;
        position: relative;
        box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        transition: background-color 0.2s ease;
    }

    .dropdown-btn:hover {
        background-color: #e60000;
    }

    .chevron {
        position: absolute;
        right: 20px;
        transition: transform 0.3s ease;
    }

    /* Gira la freccia se aperto */
    .chevron.open {
        transform: rotate(180deg);
    }

    .dropdown-list {
        /* Niente più position: absolute; così spinge i blocchi giù */
        width: 100%;
        background-color: white;
        border: 1px solid #ddd;
        border-radius: 8px;
        box-shadow: 0 4px 8px rgba(0,0,0,0.1);
        margin-top: 8px;
        overflow: hidden;
    }
</style>
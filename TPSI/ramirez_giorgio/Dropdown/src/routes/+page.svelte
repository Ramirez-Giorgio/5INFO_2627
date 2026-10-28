<script>
    import Dropdown from '../lib/components/dropdown.svelte';
    import DropdownItem from '../lib/components/item.svelte';

    let activeDropdown = null;
    let lastSelected = null;
    let alertMessage = "";

    const handleToggle = (id) => {
        activeDropdown = activeDropdown === id ? null : id;
    };

    // Ora passiamo anche il nome del blocco (es. "Regione", "Città")
    const handleSelect = (item, nomeBlocco) => {
        if (lastSelected === item) {
            // Se è il secondo click sullo stesso item, facciamo poppare il messaggio
            alertMessage = `hai selezionato la ${nomeBlocco} : ${item}`;
        } else {
            // Se è il primo click su questo item, lo salviamo in memoria ma nascondiamo il testo
            lastSelected = item;
            alertMessage = ""; 
        }
    };

    const regioni = ['Piemonte', 'Lombardia', 'Lazio', 'Campania'];
    const citta = ['Torino', 'Milano', 'Roma', 'Napoli'];
    const nazioni = ['Italia', 'Spagna', 'Francia', 'Germania'];
</script>

<main>
    <h1>DROP DOWN TESTER</h1>

    <Dropdown 
        title="Regione" 
        isOpen={activeDropdown === 'regioni'} 
        onToggle={() => handleToggle('regioni')}
    >
        {#each regioni as regione}
            <!-- Passiamo 'Regione' come secondo parametro -->
            <DropdownItem value={regione} on:click={() => handleSelect(regione, 'Regione')} />
        {/each}
    </Dropdown>

    <Dropdown 
        title="Città" 
        isOpen={activeDropdown === 'citta'} 
        onToggle={() => handleToggle('citta')}
    >
        {#each citta as c}
            <!-- Passiamo 'Città' come secondo parametro -->
            <DropdownItem value={c} on:click={() => handleSelect(c, 'Città')} />
        {/each}
    </Dropdown>

    <Dropdown 
        title="Nazione" 
        isOpen={activeDropdown === 'nazioni'} 
        onToggle={() => handleToggle('nazioni')}
    >
        {#each nazioni as nazione}
            <!-- Passiamo 'Nazione' come secondo parametro -->
            <DropdownItem value={nazione} on:click={() => handleSelect(nazione, 'Nazione')} />
        {/each}
    </Dropdown>

    <!-- Il messaggio renderizzato in grassetto -->
    {#if alertMessage}
        <div class="message-box">
            <strong>{alertMessage}</strong>
        </div>
    {/if}
</main>

<style>
    main {
        padding: 2rem;
        display: flex;
        flex-direction: column;
        align-items: flex-start;
    }

    h1 {
        font-family: 'Times New Roman', Times, serif;
        font-size: 2.2rem;
        font-weight: bold;
        margin-bottom: 2rem;
        letter-spacing: 1px;
    }

    .message-box {
        margin-top: 2rem;
        padding: 15px 20px;
        background-color: #333;
        color: white;
        border-radius: 8px;
        font-family: Arial, sans-serif;
        font-size: 1.1rem;
        box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        animation: fadeIn 0.3s ease;
    }

    /* Assicuriamoci che il tag strong faccia il suo lavoro */
    strong {
        font-weight: 900;
    }

    @keyframes fadeIn {
        from { opacity: 0; transform: translateY(-10px); }
        to { opacity: 1; transform: translateY(0); }
    }
</style>
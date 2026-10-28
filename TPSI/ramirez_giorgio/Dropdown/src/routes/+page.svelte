<script>
    import Dropdown from '../lib/components/dropdown.svelte';
    import Item from '../lib/components/item.svelte';

    let drop = null;
    let doppioclick = null;
    let messagge = "";

    const handleToggle = (id) => {
        drop = drop === id ? null : id;
    };

    const handleSelect = (item, nomeBlocco) => {
        if (doppioclick === item) {
            messagge = `hai selezionato la ${nomeBlocco} : ${item}`;
        } else {
            doppioclick = item;
            messagge = ""; 
        }
    };

    const regioni = ['Piemonte', 'Lombardia', 'Lazio', 'Campania'];
    const citta = ['Torino', 'Milano', 'Roma', 'Napoli'];
    const nazioni = ['Italia', 'Spagna', 'Francia', 'Germania'];
</script>

<h1>DROP DOWN TESTER</h1>

<Dropdown 
    nome="Regione" 
    isOpen={drop === 'regioni'} 
    onToggle={() => handleToggle('regioni')}
>
    {#each regioni as regione}
        <Item value={regione} on:click={() => handleSelect(regione, 'Regione')} />
    {/each}
</Dropdown>

<Dropdown 
    nome="Città" 
    isOpen={drop === 'citta'} 
    onToggle={() => handleToggle('citta')}
>
    {#each citta as c}
        <Item value={c} on:click={() => handleSelect(c, 'Città')} />
    {/each}
</Dropdown>

<Dropdown 
    nome="Nazione" 
    isOpen={drop === 'nazioni'} 
    onToggle={() => handleToggle('nazioni')}
>
    {#each nazioni as nazione}
        <Item value={nazione} on:click={() => handleSelect(nazione, 'Nazione')} />
    {/each}
</Dropdown>

{#if messagge}
    <div class="messaggio">
        <h2>
            <b>{messagge}</b>
        </h2>
    </div>
{/if}


<style>
    h1 {
        font-family: 'Times New Roman', Times, serif;
        font-size: 2.2rem;
        font-weight: bold;
        margin-bottom: 2rem;
        letter-spacing: 1px;
    }

    .messaggio {
        margin-top: 1.5rem;
        font-size: 1.2rem;
    }

</style>
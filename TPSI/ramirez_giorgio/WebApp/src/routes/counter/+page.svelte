<script>
    import Counter from '../../lib/components/counter.svelte'
    import DoubleCounter from '../../lib/components/double_counter.svelte'    
    let cont=0
    let cont1=0
    let numeri = [1,7,2,6,9,10]
</script>

<h1>
Pagina Counter!!!
</h1>

{#if cont<5}
<h2 class="rosso">Il valore del contatore vale : {cont}</h2>
{:else if cont >10}
<h2 class="arancione">Il valore del contatore vale : {cont}</h2>
{:else}
<h2 class="verde">Il valore del contatore vale : {cont}</h2>
{/if}
<Counter bind:counter={cont}/>


{#if cont1<5}
<h2 class="rosso">Il valore del contatore vale : {cont1}</h2>
{:else if cont1 >10}
<h2 class="arancione">Il valore del contatore vale : {cont1}</h2>
{:else}
<h2 class="verde">Il valore del contatore vale : {cont1}</h2>
{/if}
<DoubleCounter bind:counter={cont1}/>

<ul>
    {#each numeri as numero, indice}
    <li>numeri[{indice}]:{numero}</li>
    {/each}
</ul>

<style>
    .arancione{color: peru;}
    .rosso{color: red;}
    .verde{color: green;}
</style>
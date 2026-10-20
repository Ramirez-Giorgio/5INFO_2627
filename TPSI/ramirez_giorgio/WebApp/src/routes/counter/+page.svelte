<script>
    import Counter from '../../lib/components/counter.svelte'
    import DoubleCounter from '../../lib/components/double_counter.svelte'    
    let cont=0
    let cont1=0
</script>

<h1>
Pagina Counter!!!
</h1>
<h2>Il valore del contatore vale : {cont}</h2>
<Counter bind:counter={cont}/>

<h2>Il valore del double contatore vale : {cont1}</h2>
<DoubleCounter bind:counter={cont1}/>

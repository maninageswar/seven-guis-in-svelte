<script>
    let count = $state(0);

    $effect.pre(() => {
        // console.log('before update');
        console.log('before update',count);
    })

    $effect(() => {
        // console.log('after update');
        console.log('after update' ,count);
    })

</script>



<h1>count : {count}</h1>
<button onclick={()=>count++} class="bg-sky-500/90 text-white rounded-sm px-3 mt-3">count</button>

<input type="text" autofocus={false} class="todoInput border border-sky-500/90 rounded-sm focus:border-sky-500/90 focus:outline-sky-500/90"/>
<script>
    let count = $state(0);

    $inspect(count)
</script>

<input type="text" bind:value={count} class="border border-sky-500/90 rounded-sm"/>

<button onclick={()=>count++} class="bg-sky-500/90 text-white rounded-sm px-3">count</button>
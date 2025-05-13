<script>
	let todos = $state([
		{ pocus:false, done: false, text: 'finish Svelte tutorial' },
		{ pocus:false, done: false, text: 'build an app' },
		{ pocus:false, done: false, text: 'world domination' }
	]);

    let remaining = $derived(todos.filter((todo) => !todo.done).length);


    $effect(() => {
        console.log('effect')
        let todoInputs = document.querySelectorAll('.todoInput')
        // @ts-ignore
        todoInputs[todos.length-1].focus()
    })

</script>

<h1>todo's</h1>

{#each todos as todo}
    <div class="mt-3">
        <input type="checkbox" bind:checked={todo.done} class="accent-[#249cde]"/>
        <input type="text" bind:value={todo.text} autofocus={todo.pocus} class="todoInput border border-sky-500/90 rounded-sm focus:border-sky-500/90 focus:outline-sky-500/90"/>
    </div>
{/each}

<p class="my-3">{remaining} remaining</p>

<button onclick={()=>todos.push({ pocus:true, done: false, text: '' })} class="bg-sky-500/90 text-white rounded-sm px-3">add new</button>
<button onclick={()=>todos = todos.filter((todo) => !todo.done)} class="bg-sky-500/90 text-white rounded-sm px-3">clear completed</button>


 <!-- <script>
	let todos = $state([
		{id:1, pocus:false, done: false, text: 'finish Svelte tutorial' },
		{id:2, pocus:false, done: false, text: 'build an app' },
		{id:3, pocus:false, done: false, text: 'world domination' }
	]);

    let remaining = $derived(todos.filter((todo) => !todo.done).length);

</script>

<h1>todo's</h1>

{#each todos as todo (todo.id)}
    <div class="mt-3">
        <input type="checkbox" bind:checked={todo.done} class="accent-[#249cde]"/>
        <input type="text" bind:value={todo.text} autofocus={todo.pocus} class="todoInput border border-sky-500/90 rounded-sm focus:border-sky-500/90 focus:outline-sky-500/90"/>
    </div>
{/each}

<p class="my-3">{remaining} remaining</p>

<button onclick={()=>todos.push({id:todos.length + 1, pocus:true, done: false, text: '' })} class="bg-sky-500/90 text-white rounded-sm px-3">add new</button>
<button onclick={()=>todos = todos.filter((todo) => !todo.done)} class="bg-sky-500/90 text-white rounded-sm px-3">clear completed</button> -->


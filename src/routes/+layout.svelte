<script lang="ts">
	import '../app.css';
	import { goto } from '$app/navigation';
	import { page } from '$app/state';

	let { children } = $props();
</script>

<div class="mx-10">
	<h1 class="my-2 {page.url.pathname != '/' ? 'invisible' : ''}">welcome to 7GUI's</h1>
	<button onclick={() => goto('/')} class="bg-sky-500/90 text-white rounded-sm px-3 cursor-pointer">←home</button>
</div>

<div class="mx-10 mt-7">
	{@render children()}
</div>


<script>
	import './layout.css';
	import favicon from '$lib/assets/Prophetic-Insight.ico';



	let { children } = $props();
</script>

<svelte:head><link rel="icon" href={favicon} /></svelte:head>
{@render children()}


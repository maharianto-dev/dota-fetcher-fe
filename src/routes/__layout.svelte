<script>
	import '../app.css';
	import NavBar from '../lib/components/NavBar.svelte';
</script>

<div class="min-h-screen flex flex-col">
	<div class="h-24 flex min-w-full">
		<NavBar />
	</div>
	<div class="flex justify-center items-center flex-grow">
		<slot />
	</div>
</div>

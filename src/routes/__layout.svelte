<script>
	import '../app.css';
	import NavBar from '../lib/components/NavBar.svelte';
</script>

<div class="h-screen flex flex-column">
	<div class="h-24 flex">
		<NavBar />
	</div>
	<div class="flex justify-center items-center flex-grow">
		<slot />
	</div>
</div>

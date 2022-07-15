<script lang="ts">
	import Loading from '../RequestState/RequestStateLoading.svelte';

	export let requestPromise;
</script>

{#await requestPromise}
	<Loading />
{:then data}
	{#if data != null}
		<div class="flex flex-row flex-wrap justify-between gap-4">
			{#each data as datum}
				<div class="flex flex-col justify-between">
					<img class="m-0" src={datum.avatarfull} />
					<p>{datum.personaname}</p>
				</div>
			{/each}
		</div>
	{/if}
{/await}

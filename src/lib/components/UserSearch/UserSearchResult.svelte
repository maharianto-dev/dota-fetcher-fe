<script lang="ts">
	import type { UserSearchResultModel } from '$lib/models/UserSearchResult.model';
	import RequestStateLoading from '../RequestState/RequestStateLoading.svelte';

	export let requestPromise: Promise<UserSearchResultModel[]>;
</script>

{#await requestPromise}
	<RequestStateLoading />
{:then data}
	{#if data != null}
		<div class="flex flex-row flex-wrap justify-between gap-4">
			{#each data as datum}
				<div class="flex flex-col justify-between">
					<img class="m-0" src={datum.avatarfull} alt="avatar" />
					<p>{datum.personaname}</p>
				</div>
			{/each}
		</div>
	{/if}
{/await}

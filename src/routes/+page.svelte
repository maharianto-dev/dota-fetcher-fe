<script lang="ts">
	import { hostname } from '$lib/stores/environment';
	import UserSearchInput from '$lib/components/UserSearch/UserSearchInput.svelte';
	import UserSearchResult from '$lib/components/UserSearch/UserSearchResult.svelte';
	import type { UserSearchResultModel } from '$lib/models/UserSearchResult.model';

	let steamId: string;
	let username: string;

	let buttonUserNameSearchClick$: Promise<UserSearchResultModel[]>;

	const onButtonSearchClick = async () => {
		const url = `${hostname}/search-match-history-by-player-id?${new URLSearchParams({
			id: steamId
		})}`;
		const response = await fetch(url);
		const data = await response.json();
	};

	const onButtonUserNameSearchClick = () => {
		buttonUserNameSearchClick$ = getUserByUserNameSearch();
	};

	const getUserByUserNameSearch = async () => {
		const url = `${hostname}/get-user-by-username?${new URLSearchParams({
			username: username
		})}`;

		const response = await fetch(url);
		const data = await response.json();

		return data;
	};
</script>

<div class="flex flex-col w-8/12">
	<h1>Match History Search</h1>
	<div class="form-control w-full my-2">
		<label class="label">
			<span class="label-text">What is your steam id? (ex: 100666410)</span>
		</label>
		<input
			type="text"
			placeholder="Insert Steam Id"
			class="input input-bordered w-full"
			bind:value={steamId}
		/>
	</div>
	<div />
	<div class="flex flex-row ml-auto">
		<button class="btn btn-accent w-24" on:click={onButtonSearchClick}> Search </button>
	</div>

	<h1>User Search</h1>
	<UserSearchInput bind:query={username} />
	<div />
	<div class="flex flex-row ml-auto">
		<button class="btn btn-accent w-24" on:click={onButtonUserNameSearchClick}> Search </button>
	</div>

	<div class="my-4">
		<UserSearchResult bind:requestPromise={buttonUserNameSearchClick$} />
	</div>
</div>

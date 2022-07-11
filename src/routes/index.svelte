<script lang="ts">
  let steamId;
  
  const onButtonSearchClick = async () => {
    const url = `http://localhost:8080/search-match-history-by-player-id?${new URLSearchParams({
      id: steamId
    })}`;
    // const url = `http://localhost:8080/ping`
    const response = await fetch(url)
    const data = await response.json();
    console.log('~ 🚀 ~ Class: , Function: onButtonSearchClick, Line 10 data: ', data);
  }
</script>

<div class="flex flex-col w-8/12">
  <h1>Match History Search</h1>
  <div class="form-control w-full my-2">
    <label class="label">
      <span class="label-text">What is your steam id? (ex: 100666410)</span>
    </label>
    <input type="text" placeholder="Insert Steam Id" class="input input-bordered w-full" bind:value={steamId}/>
  </div>
  <div></div>
  <div class="flex flex-row ml-auto">
    <button class="btn btn-accent w-24" on:click={onButtonSearchClick}>
      Search
    </button>
  </div>
</div>

<script lang="ts">
  export let query;
</script>

<div class="form-control w-full my-2">
  <label class="label">
    <span class="label-text">Insert username</span>
  </label>
  <input type="text" placeholder="Insert username" class="input input-bordered w-full" bind:value={query}/>
</div>

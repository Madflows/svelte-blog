<script>
  import MdRefresh from 'svelte-icons/md/MdRefresh.svelte';


  let number = 1;
  const increment = () => {
    number += 5;
  };
  $: multiple = number * 2;
  $: division = number / 2;
</script>

<main class="flex flex-col gap-3 items-center justify-center min-h-screen">
  <h1>The number is {number}</h1>
  <h2 class="text-lg">{number} * 2 = {multiple}</h2>
  <h2>{number} / 2 = {division}</h2>

  <div class="flex items-center justify-center space-x-3">
    <button on:click={increment} class="btn btn-primary">Add 5</button>
    <button disabled={number == 1} on:click={() => (number = 1)} class="btn text-white p-2"><MdRefresh /></button>
  </div>

  <div class="flex flex-col gap-3">
    {#if number >= 10 && number <= 20}
      <div class="alert alert-success shadow-lg shadow-emerald-300">
        <div>
          <span>Numbers look good!</span>
        </div>
      </div>
    {:else if number > 20}
      <div class="alert alert-error shadow-lg shadow-red-300">
        <div>
          <span>Numbers are too high!</span>
        </div>
      </div>
    {:else}
      <div class="alert alert-warning shadow-lg shadow-orange-200">
        <div>
          <span>Number may be too low!</span>
        </div>
      </div>
    {/if}
  </div>
</main>

<style>
</style>

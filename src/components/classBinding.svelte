<script>
  let active = 1;

  function changeActive(activeNum) {
    active = activeNum;
  }
</script>

<main
  class="min-h-screen w-full bg-slate-700 text-white flex items-center justify-center"
>
  <div class="btn-group">
    <button
      on:click={() => changeActive(1)}
      class="btn btn-lg {active === 1 && 'btn-active'}">Home</button
    >
    <button
      on:click={() => changeActive(2)}
      class="btn btn-lg {active === 2 && 'btn-active'}">Product</button
    >
    <button
      on:click={() => changeActive(3)}
      class="btn btn-lg {active === 3 && 'btn-active'}">Dataset</button
    >
    <button
      on:click={() => changeActive(4)}
      class="btn btn-lg {active === 4 && 'btn-active'}">Menu</button
    >
  </div>
</main>

<style>
</style>

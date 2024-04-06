<script lang="ts">
  import Modal from './Modal.svelte';

  let modalOpen = false;
  let duration: number = 500;
  const close = () => {
    modalOpen = false;
  };
</script>

<div class="mx-auto my-8 max-w-lg px-4">
  <div class="space-y-4">
    <h1 class="text-2xl">Svelte 4.2.12</h1>

    <p>
      Open up dev tools and look at the transition tween values (i.e. the translate y %) when you
      open or close the modal. In Svelte 4 the last value is always correct (0 or 100.)
    </p>

    <p>
      Transition Duration: <input type="number" class="bg-white text-black" bind:value={duration} />
    </p>
    <p>
      <button class="text-5xl underline" on:click={() => (modalOpen = true)}>Open Modal</button>
    </p>

    <p>To see the bad behavior in Svelte 5 do:</p>
    <pre>
      git switch main
      pnpm i
      pnpm dev
    </pre>
  </div>
</div>

{#if modalOpen}
  <Modal {close} {duration} />
{/if}

<script lang="ts">
	import Modal from './Modal.svelte';

	let modalOpen = $state(false);
  let duration: number = $state(500);
  const close = () => {
    modalOpen = false;
  }
</script>

<div class="container mx-auto my-8 px-4">
	<div class="space-y-4">
		<h1>Welcome to SvelteKit</h1>
		<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>

    <p>
      Tranistion Duration: <input type="number" class="bg-white text-black" bind:value={duration}/>
    </p>
		<p>
			<button class="underline" onclick={() => modalOpen = true}>Open Modal</button>
		</p>
	</div>
</div>

{#if modalOpen}
	<Modal {close} {duration} />
{/if}

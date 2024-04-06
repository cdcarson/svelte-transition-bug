<script lang="ts">
	import Modal from './Modal.svelte';

	let modalOpen = $state(false);
	let duration: number = $state(500);
	const close = () => {
		modalOpen = false;
	};
</script>

<div class="mx-auto my-8 max-w-lg px-4">
	<div class="space-y-4">
		<h1 class="text-2xl">Svelte 5.0.0-next.95</h1>

		<p>
			Open up dev tools and look at the transition values (i.e. the translate y %) when you open or
			close the modal. In Svelte 5, when the duration is less than ~500, the last value is incorrect (greater than 0 or
			less than 100.) 
		</p>

		<p>
			Transition Duration: <input type="number" class="bg-white text-black" bind:value={duration} />
		</p>
		<p>
			<button class="text-5xl underline" on:click={() => (modalOpen = true)}>Open Modal</button>
		</p>

		<p>To see that this bug does not happen in Svelte 4 do:</p>
		<pre>
      git switch svelte-4
      pnpm i
      pnpm dev
    </pre>
	</div>
</div>

{#if modalOpen}
	<Modal {close} {duration} />
{/if}

<script lang="ts">
  import { sineInOut } from 'svelte/easing';
  type P = {
    close: () => void;
    duration: number;
  };
  let { close, duration }: P = $props();

  const modalSlide = (_node: HTMLElement, { duration = 500 }) => {
    const mediaQuery = window.matchMedia('(prefers-reduced-motion: reduce)');
    const calculatedDuration = mediaQuery && mediaQuery.matches ? 0 : duration;
    return {
      delay: 0,
      duration: calculatedDuration,
      css: (t: number) => {
        let tyPct = 100 - sineInOut(t) * 100;
        console.log(tyPct);
        // if (tyPct > 99.5) {
        //   tyPct = 100
        // } else if (tyPct < .5) {
        //   tyPct = 0;
        // }
        return `transform: translateY(${tyPct}%)`;
      }
    };
  };

  const handleKeydown = (event: KeyboardEvent) => {
    if ('Escape' === event.key) {
      close();
    }
  };
</script>

<svelte:window onkeydown={handleKeydown} />
<div class="modal" transition:modalSlide|global={{ duration }}>
  <button type="button" class="underline" onclick={close}>Close</button> (or press <kbd>esc</kbd>)
</div>

<style lang="postcss">
  .modal {
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    z-index: 1;
    background-color: #fff;
    color: #000;
    padding: 1rem;
  }
</style>

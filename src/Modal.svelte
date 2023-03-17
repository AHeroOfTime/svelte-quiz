<script>
  import { fly, fade } from 'svelte/transition';
  import { createEventDispatcher } from 'svelte';

  let w;
  const dispatch = createEventDispatcher();
</script>

<style lang="scss">
  .modal-bg {
    height: 100vh;
    position: fixed;
    top: 0;
    right: 0;
    bottom: o;
    left: 0;
    background: rgba(0, 0, 0, 0.8);
    .modal {
      background: white;
      padding: 20px;
      border-radius: 15px;
    }
  }

</style>

<div class="modal-bg" transition:fade bind:clientWidth={w}>
  <div class="modal" transition:fly={{y: -100}}>
    <button on:click={() => {
      dispatch('close')
    }}>Close</button>
    <!-- <slot>optional fallback</slot> -->
    <!-- <slot /> generic slot -->
    <!-- <slot name="modal" /> named slot -->
    width: {w}
    <slot />
  </div>
</div>

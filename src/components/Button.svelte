<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
  export let style = "primary";
  export let type = "button";
  export let disabled = "true";
  function clickHandler(e) {
    dispatch("add-feedback");
  }
</script>

<button {type} class={style} {disabled} on:click={clickHandler}>
  <slot />
</button>

<style>
  button {
    color: #fff;
    border: 0;
    border-radius: 8px;
    color: #fff;
    width: 100px;
    height: 40px;
    cursor: pointer;
  }
  .primary {
    background-color: #202142;
  }
  .secondary {
    background: #ff6a95;
  }
  button:hover {
    transform: scale(0.98);
    opacity: 0.9;
  }
  button:disabled {
    background-color: #cccccc;
    color: #333;
    cursor: not-allowed;
  }
  button:disabled:hover {
    transform: scale(1);
    opacity: 1;
  }
</style>

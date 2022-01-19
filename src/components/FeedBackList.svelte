<script>
  import FeedBackItem from "./FeedBackItem.svelte";
  import { fade, scale } from "svelte/transition";
  export let feedBacks = [];
</script>

<main>
  {#each feedBacks as feedBack (feedBack.id)}
    <div in:scale out:fade>
      <FeedBackItem {feedBack} on:delete-feedback />
    </div>
  {/each}
</main>

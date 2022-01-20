<script>
  import { FeedbackStore } from "../store";
  import FeedBackItem from "./FeedBackItem.svelte";
  import { fade, scale } from "svelte/transition";
</script>

<main>
  {#each $FeedbackStore as feedBack (feedBack.id)}
    <div in:scale out:fade>
      <FeedBackItem {feedBack} />
    </div>
  {/each}
</main>

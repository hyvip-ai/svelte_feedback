<script>
  import { FeedbackStore } from "../store";
  import Card from "./Card.svelte";
  export let feedBack = { id: 0, rating: 0, text: "" };
  const handleDelete = (itemId) => {
    const newFeedBacks = $FeedbackStore.filter((item) => item.id !== itemId);
    FeedbackStore.update(() => {
      return [...newFeedBacks];
    });
  };
</script>

<Card>
  <div class="num-display">
    {feedBack.rating}
  </div>
  <button
    on:click={() => {
      handleDelete(feedBack.id);
    }}
    class="close"
  >
    X
  </button>
  <p class="text-display">
    {feedBack.text}
  </p>
</Card>

<style>
  .num-display {
    position: absolute;
    top: -10px;
    left: -10px;
    width: 50px;
    height: 50px;
    background: #ff6a95;
    color: #fff;
    border: 1px #eee solid;
    border-radius: 50%;
    padding: 10px;
    text-align: center;
    font-size: 19px;
  }
  .close {
    position: absolute;
    top: 10px;
    right: 20px;
    cursor: pointer;
    background: none;
    border: none;
  }
</style>

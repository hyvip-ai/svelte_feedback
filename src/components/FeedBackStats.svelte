<script>
  import { FeedbackStore } from "../store";
  let feedBacks = [];
  FeedbackStore.subscribe((data) => {
    feedBacks = [...data];
  });
  $: average = feedBacks.length?feedBacks.reduce((acc, item) => {
      return (acc += item.rating);
    }, 0) / feedBacks.length:0
  $: numerofFeedbacks = feedBacks.length;
</script>

<div class="feedback-stats">
  <h4>{numerofFeedbacks} Reviews</h4>
  <h4>Ratings Average : {average}</h4>
</div>

<style>
  .feedback-stats {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
</style>

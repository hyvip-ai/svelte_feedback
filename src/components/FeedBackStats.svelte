<script>
  import { FeedbackStore } from "../store";
  $: average = $FeedbackStore.length?Math.floor(($FeedbackStore.reduce((acc, item) => {
      return (acc += item.rating);
    }, 0) / $FeedbackStore.length)*10)/10:0
  $: numerofFeedbacks = $FeedbackStore.length;
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

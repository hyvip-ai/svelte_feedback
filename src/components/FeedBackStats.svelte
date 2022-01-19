<script>
  export let average;
  export let numerofFeedbacks;
</script>

<div class="feedback-stats">
  <h4> {numerofFeedbacks} Reviews</h4>
  <h4>Ratings Average : {average}</h4>
</div>

<style>
  .feedback-stats {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
</style>

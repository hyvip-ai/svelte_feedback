<script>
  import Button from "./Button.svelte";
  import Card from "./Card.svelte";
  import RatingSelect from "./RatingSelect.svelte";
  import { FeedbackStore } from "../store";
  let btn_disabled = true;
  let message = "";
  let min = 10;
  let rating = 10;
  function checkWords(e) {
    message = !(e.target.value.trim().length >= min)
      ? `FeedBack Must have ${min} charecters`
      : "";
    btn_disabled = message ? true : false;
  }
  function blurHandler(e) {
    if (e.target.value.trim().length === 0) {
      message = "";
    }
  }
  function addRating(e) {
    rating = Number(e);
  }
  function addFeddback() {
    let text = document.getElementById("feedback").value;
    document.getElementById("feedback").value = "";
    let newFeedBack = { id: $FeedbackStore.length + 1, rating, text };
    FeedbackStore.update((prev) => {
      return [newFeedBack, ...prev];
    });
    rating = 10;
  }
</script>

<Card>
  <header>
    <h2>How would you rate your service with us?</h2>
  </header>
  <form on:submit|preventDefault>
    <RatingSelect {rating} {addRating} on:rating-select={addRating} />
    <div class="input-group">
      <input
        id="feedback"
        type="text"
        on:input={checkWords}
        placeholder="Tell Us Something that keeps you coming back"
        on:blur={blurHandler}
        autocomplete="off"
      />
      <Button
        type={"submit"}
        disabled={btn_disabled}
        on:add-feedback={addFeddback}>Send</Button
      >
    </div>
    <div class="message">
      {message}
    </div>
  </form>
</Card>

<style>
  header {
    max-width: 400px;
    margin: auto;
  }
  header h2 {
    font-size: 22px;
    font-weight: 600;
    text-align: center;
  }
  .input-group {
    display: flex;
    flex-direction: row;
    border: 1px solid #ccc;
    padding: 8px 10px;
    border-radius: 8px;
    margin-top: 15px;
  }
  input {
    flex-grow: 2;
    border: none;
    font-size: 16px;
  }
  input:focus {
    outline: none;
  }
  .message {
    padding-top: 10px;
    text-align: center;
    color: rebeccapurple;
  }
</style>

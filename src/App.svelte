<script>
  import FeedBackForm from "./components/FeedBackForm.svelte";

  import FeedBackList from "./components/FeedBackList.svelte";
  import FeedBackStats from "./components/FeedBackStats.svelte";

  let feedBacks = [
    {
      id: 1,
      rating: 10,
      text: "Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.",
    },
    {
      id: 2,
      rating: 9,
      text: "Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.",
    },
    {
      id: 3,
      rating: 8,
      text: "Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.",
    },
  ];
  const deleteFeedBack = (e) => {
    feedBacks = feedBacks.filter((item) => {
      return item.id !== e.detail;
    });
  };
  $: totalFeedBacks = feedBacks.length;
  $: average = feedBacks.length
    ? feedBacks.reduce((acc, item) => {
        return (acc += item.rating);
      }, 0) / feedBacks.length
    : 0;
  function addToArray(e) {
    let newItem = { ...e.detail, id: feedBacks.length + 1 };
    feedBacks = [newItem, ...feedBacks];
  }
</script>

<main class="container">
  <FeedBackForm on:add-array={addToArray} />
  <FeedBackStats {average} numerofFeedbacks={totalFeedBacks} />
  <FeedBackList {feedBacks} on:delete-feedback={deleteFeedBack} />
</main>

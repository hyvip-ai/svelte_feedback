<script>
import FeedBackItem from "./FeedBackItem.svelte";


    export let feedBacks=[]
</script>
<main>
    {#each feedBacks as feedBack (feedBack.id)}
    <FeedBackItem feedBack={feedBack} on:delete-feedback/>
    {/each}
</main>
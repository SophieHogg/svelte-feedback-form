<script>
  import { fly, scale } from 'svelte/transition'
  import FeedbackItem from "./FeedbackItem.svelte";
  export let feedback=[];

</script>

{#each feedback as fb (fb.id)}
<div in:scale out:fly>
  <FeedbackItem item={fb} on:delete-feedback/>
</div>
{/each}
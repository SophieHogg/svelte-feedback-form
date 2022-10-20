<script>
  import {createEventDispatcher} from 'svelte';
  import Card from "./Card.svelte";
   export let item;

   const dispatch = createEventDispatcher();
  

   let rating = item.rating;
   $:numcolor = rating<6 ?'#c25100':'#00a20d';

   const handleDelete = (itemId) =>{
    dispatch('delete-feedback',itemId)
   }
</script>

<Card>
  <div style="background-color: {numcolor};"class="num-display">
    {item.rating}
  </div>
  <!--A personal change to ensure numbers 5 and under display in red.-->
  <button class="close" on:click={()=>handleDelete(item.id)}>
    X
  </button>
  <p class="text-display">
    {item.text}
  </p>
</Card>

<style>
    .num-display {
    position: absolute;
    top: -10px;
    left: -10px;
    width: 50px;
    height: 50px;
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
    font-size: 20px;
    cursor: pointer;
    background: none;
    border: none;
  }

</style>
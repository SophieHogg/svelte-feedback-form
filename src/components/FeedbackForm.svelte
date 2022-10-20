<script>
  import Button from "./Button.svelte";
  import Card from "./Card.svelte"
  import RatingSelect from "./RatingSelect.svelte"
  import { createEventDispatcher } from "svelte";
  import {v4 as uuidv4} from 'uuid';
 

  const dispatch = createEventDispatcher();
  let buttonDis = true;
  let text='';
  let min = 10;
  let message ='';
  let rating = 10;


  const handleSelect = e => rating = (e.detail);

  const handleInput = ()=>{
    if(text.trim().length<=min){
      message = `Text must be at least ${min} characters`
      buttonDis=true;
    }
    else{
      message='';
      buttonDis=false;
    }
  }

  const handleSubmit =()=>{
    if(text.trim().length>=min){
      const newFeedback = {
        id: uuidv4(),
        text,
        rating: +rating
      }
          dispatch('add-feedback',newFeedback)
          text='';
    }
  }
</script>

<Card>
<header>
  <h2>How would you rate your experience?</h2>
</header>
<form on:submit|preventDefault={handleSubmit}>
   <RatingSelect on:rating={handleSelect}/>
  <div class="input-group">
    <input type="text" placeholder="Tell us how you feel." on:input={handleInput} bind:value ={text}>
    <Button disabled={buttonDis} type="submit">Submit</Button>
  </div>
  {#if message}
  <div class="message">{message}</div>
  {/if}
  </form>
  </Card>

<style>
  header {
    max-width: 500px;
    margin: auto;
  }

  header h2 {
    font-size: 22px;
    font-weight: 600;
    text-align: center;
    color: #003d05;
  }

  .input-group {
    display: flex;
    flex-direction: row;
    border: 3px solid #00a20d;
    padding: 8px 10px;
    border-radius: 8px;
    margin-top: 15px;
  }

  input {
    flex-grow: 2;
    border: none;
    font-size: 16px;
    background-color: #cceddb;
  }

  input:focus {
    outline: none;
  }

  .message{
    padding-top: 10px;
    text-align: center;
    color: #003d3a;
  }
</style>
<script>
  import {createEventDispatcher} from 'svelte';

  let selected=10;

  const dispatch = createEventDispatcher()

  const onChange=(e)=>{
    selected = e.currentTarget.value;
    dispatch('rating', selected)
  }
</script>

<ul class="rating">
  <li>
    <input type="radio" id="rate1" name="rating" value="1" on:change={onChange} checked={selected===1}/>
    <label for="rate1">1</label>
  </li>

  <li>
    <input type="radio" id="rate2" name="rating" value="2" on:change={onChange} checked={selected===2}/>
    <label for="rate2">2</label>
  </li>

  <li>
    <input type="radio" id="rate3" name="rating" value="3" on:change={onChange} checked={selected===3}/>
    <label for="rate3">3</label>
  </li>
  
  <li>
    <input type="radio" id="rate4" name="rating" value="4" on:change={onChange} checked={selected===4}/>
    <label for="rate4">4</label>
  </li>
  
  <li>
    <input type="radio" id="rate5" name="rating" value="5" on:change={onChange} checked={selected===5}/>
    <label for="rate5">5</label>
  </li>
  
  <li>
    <input type="radio" id="rate6" name="rating" value="6" on:change={onChange} checked={selected===6}/>
    <label for="rate6">6</label>
  </li>
  
  <li>
    <input type="radio" id="rate7" name="rating" value="7" on:change={onChange} checked={selected===7}/>
    <label for="rate7">7</label>
  </li>
  
  <li>
    <input type="radio" id="rate8" name="rating" value="8" on:change={onChange} checked={selected===8}/>
    <label for="rate8">8</label>
  </li>
  
  <li>
    <input type="radio" id="rate9" name="rating" value="9" on:change={onChange} checked={selected===9}/>
    <label for="rate9">9</label>
  </li>
  
  <li>
    <input type="radio" id="rate10" name="rating" value="10" on:change={onChange} checked={selected===10}/>
    <label for="rate10">10</label>
  </li>
</ul>

<style>
  .rating {
    display: flex;
    align-items: center;
    justify-content: space-around;
    margin: 30px 0;
  }

  .rating li {
    position: relative;
    background: #f4f4f4;
    width: 50px;
    height: 50px;
    padding: 10px;
    text-align: center;
    border-radius: 50%;
    font-size: 19px;
    border: 1px #eee solid;
    transition: 0.1s;
  }

  .rating li label {
    position: absolute;
    top: 50%;
    left: 50%;
    width: 50px;
    height: 50px;
    padding: 10px;
    border-radius: 50%;
    transform: translate(-50%, -50%);
    cursor: pointer;
  }

  .rating li:hover {
    background: #3ba043;
    color: #fff;
  }

  /* Make actual radio select invisible */
  [type='radio'] {
    opacity: 0;
  }

  /* Use the sibling select */
  [type='radio']:checked ~ label {
    background: #155c1b;
    color: #fff;
  }
</style>
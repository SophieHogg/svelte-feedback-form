<script>
  export let count;
  export let average;

</script>

<div class="feedback-stats">
  <h3>{count} Reviews</h3>
  <h3>Average Score: {average}</h3>
</div>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Noto+Sans+Warang+Citi&display=swap');
  .feedback-stats{
    display: flex;
    justify-content: space-around;
    font-family: 'Noto Sans Warang Citi', sans-serif;
  }
</style>
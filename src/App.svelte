<script>
	import FeedbackList from './components/FeedbackList.svelte'
	import FeedbackStats from './components/FeedbackStats.svelte';
	import FeedbackForm from './components/FeedbackForm.svelte';

	const addFeedback = (e)=>{
		const newFeedback = e.detail;
		feedback = [newFeedback, ...feedback]
	}
	const deleteFeedback = (e)=>{
		const itemId=e.detail
		feedback = feedback.filter((item)=>item.id!=itemId)
	}

	let feedback = [
		{
			id:1,
			rating: 7,
			text: 'Food was amazing but service was not up to par.'
		},
		{
			id:2,
			rating: 8,
			text: 'Great food, great experience - music was a bit too loud'
		},
		{
			id:3,
			rating: 10,
			text:'I come here every year and love it every time!! Can\'t recommend this place more. Would recommend the nori tacos especially.'
		},
		{
			id:4,
			rating: 3,
			text: 'This place sucks.'
		}
	]

$:count = feedback.length;
$:average=count>0?(feedback.reduce((a, {rating})=>a+rating,0)/count):0;
//a personal addition to stop it from displaying NaN if all functions are deleted.



</script>

<main class="container">
	<FeedbackForm on:add-feedback={addFeedback}/>
	<FeedbackStats {count} {average}/>
	<FeedbackList {feedback} on:delete-feedback={deleteFeedback}/>

</main>

<style>

</style>
<script>
	import Header from './components/Header.svelte';
	import Footer from './components/Footer.svelte';
	import Tabs from './shared/Tabs.svelte';
	import CreatePollForm from './components/CreatePollForm.svelte'
	import PollList from './components/PollList.svelte'

	let items = ['Current Polls', 'Add New Polls'];
	let activeItem = 'Current Polls';

	const tabChange = (e) => {
		activeItem = e.detail;
	}

	let polls = [
		{
			id: 1,
			question: "Python or JavaScript",
			answerA: "Python",
			answerB: "JavaScript",
			votesA: 9,
			votesB: 11
		}
	];

	const handleAddPoll = (e) => {
		const poll = e.detail;
		polls = [...polls, poll];
		activeItem = 'Current Polls';
	}
</script>

<Header />
	<main>

		<Tabs {items} {activeItem} on:tabChange={tabChange}/>

		{#if activeItem === 'Current Polls'}

			<PollList {polls} />

		{:else if activeItem === 'Add New Polls'}

			<CreatePollForm on:add={handleAddPoll}/>

		{/if}

	</main>
<Footer />

<style>
	main {
		margin: 40px auto;
		max-width:960px;
	}
</style>


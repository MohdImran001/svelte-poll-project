<script>
	import Tabs from './shared/Tabs.svelte';
	import CreatePollForm from './components/CreatePollForm.svelte'
	import PollList from './components/PollList.svelte'

	let items = ['Current Polls', 'Add New Polls'];
	let activeItem = 'Current Polls';

	const tabChange = (e) => {
		activeItem = e.detail;
	}

	const handleAddPoll = (e) => {
		activeItem = 'Current Polls';
	}

</script>

	<main>

		<Tabs {items} {activeItem} on:tabChange={tabChange}/>

		{#if activeItem === 'Current Polls'}

			<PollList />

		{:else if activeItem === 'Add New Polls'}

			<CreatePollForm on:add={handleAddPoll}/>

		{/if}

	</main>

<style>
	main {
		margin: 40px auto;
		max-width:960px;
	}
</style>


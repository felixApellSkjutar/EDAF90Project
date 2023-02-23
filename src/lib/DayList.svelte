<script lang="ts">
	import { Spinner } from 'flowbite-svelte';
	import EventCard from './EventCard.svelte';
	import { getDay } from './fetch';
	import type { Event } from './types';

	export let date: Date;

	const exampleList = async (): Promise<Event[]> => {
		const a = await getDay(date);
		return a;
	};

	const dayString = () => {
		let day = new Date();
		console.log(day.toDateString(), date.toDateString());
		if (date.toDateString() === day.toDateString()) {
			return 'Today';
		}
		day.setDate(day.getDate() + 1);
		if (date.toDateString() === day.toDateString()) {
			return 'Tomorrow';
		}
		return date.getDate() + '/' + (date.getMonth() + 1);
	};
</script>

<p class="text-4xl font-extrabold mb-3 dark:text-white mt-10">{dayString()}</p>
<div class="grid gap-4 grid-cols-3 auto-cols-auto">
	{#await exampleList()}
		<Spinner />
	{:then list}
		{#each list as event}
			<EventCard {event} />
		{/each}
	{/await}
</div>

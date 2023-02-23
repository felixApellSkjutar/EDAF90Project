<script lang="ts">
	import DayList from '$lib/DayList.svelte';
	import EventCard from '$lib/EventCard.svelte';
	import EventPopup from '$lib/EventPopup.svelte';
	import { getDay } from '$lib/fetch';
	import Header from '$lib/Header.svelte';
	import type { Event } from '$lib/types';

	const exampleList = async (): Promise<Event[]> => {
		const a = await getDay(new Date('2023-02-23'));
		console.log(a[0]);
		return a;
	};

	let open = false;
	const today = new Date();
</script>

<div class="flex justify-center">
	<div class="max-w-screen-lg">
		<Header />
		<DayList date={today} />
		<DayList date={new Date(new Date().setDate(today.getDate() + 1))} />
		<DayList date={new Date(new Date().setDate(today.getDate() + 2))} />
		<DayList date={new Date(new Date().setDate(today.getDate() + 3))} />
		<DayList date={new Date(new Date().setDate(today.getDate() + 4))} />
	</div>
</div>

<button on:click={() => (open = true)}>Show modal</button>

<!-- {#await exampleList() then list}
	<EventPopup event={list[0]} />
{/await} -->

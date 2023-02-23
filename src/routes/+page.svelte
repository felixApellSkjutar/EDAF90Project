<script lang="ts">
	import EventCard from '$lib/EventCard.svelte';
	import EventPopup from '$lib/EventPopup.svelte';
	import { getDay } from '$lib/fetch';
	import type { Event } from '$lib/types';
	import { Button, Card, DarkMode, Modal, Spinner } from 'flowbite-svelte';

	const exampleList = async (): Promise<Event[]> => {
		const a = await getDay(new Date('2023-02-23'));
		console.log(a[0]);
		return a;
	};

	let open = false;
</script>

<div class="flex justify-center">
	<div class="max-w-screen-lg">
		<DarkMode class="dark:text-white" />
		<div class="grid gap-4 grid-cols-3 auto-cols-auto">
			<!-- <div class="w-60 h-72 bg-green-200 " /> -->
			{#await exampleList()}
				<Spinner />
			{:then list}
				{#each list as event}
					<EventCard {event} />
				{/each}
			{/await}
		</div>
	</div>
</div>

<button on:click={() => (open = true)}>Show modal</button>

<!-- {#await exampleList() then list}
	<EventPopup event={list[0]} />
{/await} -->

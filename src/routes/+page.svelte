<script lang="ts">
	import EventPopup from '$lib/EventPopup.svelte';
	import { getDay } from '$lib/fetch';
	import Test from '$lib/Test.svelte';
	import { Button, DarkMode, Modal } from 'flowbite-svelte';

	const exampleList = async () => {
		const a = await getDay(new Date('2023-02-23'));
		return a;
	};

	let open = false;
</script>

<div class="border-2 w-screen-sm">
	<DarkMode class="dark:text-white" />
	<Test name={'Joel'} />
	<p class="dark:text-white">
		Visit <a class="font-bold underline" href="https://kit.svelte.dev">kit.svelte.dev</a> to read the
		documentation
	</p>
	<div class="p-8">
		<Button gradient color="cyanToBlue">Snygg knapp</Button>
	</div>
</div>

<button on:click={() => (open = true)}>Show modal</button>

<Modal bind:open>
	{#await exampleList() then list}
		<EventPopup event={list[0]} />
	{/await}
</Modal>

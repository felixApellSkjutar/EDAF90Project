<script lang="ts">
	import {  Modal } from 'flowbite-svelte'
	import {Button, ButtonGroup} from 'flowbite-svelte'
	import Heart from './heartOutline.svelte'
	import FilledHeart from './heartFilled.svelte'

	let defaultModal = true;

	let h = Heart
	export let event: any;

	console.log(Object.keys(event).map((key) => {
			return `${key}: ${event[key]}`;
		}).reduce((prev, next) => `${prev} \n${next}`,'' ));

	const description= event['description'];
	const summary = event['summary'];

	const organizer = event['organizer'];
	const email = organizer['email'];
	console.log(event['date']);
	const {start, end, updated} = event['date'];
	const location = event['location']
	let b = true
	function likeEvent() {
		b = !b;
	}
</script>


<Modal title={`${organizer['name']}: ${summary}`} bind:open={defaultModal} autoclose>


	  <svelte:fragment slot='default'>
		BALLABALLABALAL
		<p class="text-base leading-relaxed text-gray-500 dark:text-gray-400">
			{description}
		  </p>

		  <p>
			start: {start}, end: {end}, location: {location}
		  </p>
	  </svelte:fragment>
	  <svelte:fragment slot='footer'>
		<ButtonGroup class="space-x-px">
			<Button gradient color="purpleToBlue">Book</Button>
			<Button gradient color="greenToBlue"> <a href={`mailto:${email}`}> email </a></Button>
			<Button on:click={likeEvent} gradient color= "cyanToBlue">			
				{#if b}
					<Heart />
				{:else}
					<FilledHeart />
				{/if}
			</Button>
		</ButtonGroup>
		<!-- <button on:click={likeEvent}>
			{#if b}
				<Heart />
			{:else}
				<FilledHeart />
			{/if}
		</button> -->
		
	  </svelte:fragment>

</Modal>


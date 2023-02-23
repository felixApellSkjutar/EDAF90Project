<script lang="ts">
	import { Card } from 'flowbite-svelte';
	import type { Event } from './types';

	export let event: Event;
</script>

<Card img={event.image_url}>{event.summary}</Card>

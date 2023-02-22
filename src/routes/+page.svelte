<script>
	import Test from '$lib/Test.svelte';
	import { Button, DarkMode } from 'flowbite-svelte';
</script>

<DarkMode class="dark:text-white" />
<Test name={'Joel'} />
<p class="dark:text-white">
	Visit <a class="font-bold underline" href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation
</p>
<div class="p-8">
	<Button gradient color="cyanToBlue">Snygg knapp</Button>
</div>

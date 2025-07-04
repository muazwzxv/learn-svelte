<script>
	import Button from '$lib/components/Button.svelte';
	import { AlarmClock, Search } from 'lucide-svelte';
</script>

<!-- 
one way to do it

{#snippet left()}
	<Search />
{/snippet}

<Button {left}>Children text</Button> 
-->

<Button>
	{#snippet left()}
		<Search />
	{/snippet}
	Text

	{#snippet right()}
		<AlarmClock />
	{/snippet}
</Button>

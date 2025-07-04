<script lang="ts">
	import Button from '$lib/components/Button.svelte';
	import { AlarmCheck, AlarmClock, Search } from 'lucide-svelte';
</script>

<!-- 
one way to do it

{#snippet left()}
	<Search />
{/snippet}

<Button {left}>Children text</Button> 
-->

<Button>
	{#snippet left(isHover: boolean)}
		{#if isHover}
			<Search />
		{:else}
			<AlarmCheck />
		{/if}
	{/snippet}

	{#snippet children(isHover)}
		{#if isHover}
			Bitch i'm hovering
		{:else}
			Fuck you, I'll pop your head off
		{/if}
	{/snippet}

	{#snippet right()}
		<AlarmClock />
	{/snippet}
</Button>

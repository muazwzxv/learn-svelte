<script>
	import Button from '$lib/components/Button.svelte';
	import { Search } from 'lucide-svelte';
</script>

{#snippet bottonLeft()}
	<Search />
{/snippet}

<Button left={bottonLeft}>Children text</Button>

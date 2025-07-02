<script lang="ts">
	import type { Snippet } from 'svelte';

	interface Props {
		left?: Snippet;
		children: Snippet;
	}
	let { left, children }: Props = $props();
</script>

<!-- {#snippet sum(a: number, b: number)}
	<span>{a} + {b} = {@render bold(a + b)}</span>
{/snippet}

{#snippet bold(x: any)}
	<b>{x}</b>
{/snippet} -->

<div>
	<button>
		{#if left}
			<div class="left-content">
				{@render left()}
			</div>
		{/if}

		{@render children()}
	</button>
</div>

<style>
	button {
		border: none;
		background-color: red;
		color: aliceblue;
		padding: 0 20px;
		height: 45px;
		font-weight: bold;
		border-radius: 5px;
		cursor: pointer;
	}
</style>

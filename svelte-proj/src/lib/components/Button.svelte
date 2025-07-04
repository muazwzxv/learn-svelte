<script lang="ts">
	import { Ribbon } from 'lucide-svelte';
	import type { Snippet } from 'svelte';

	interface Props {
		left?: Snippet;
		right?: Snippet;
		children: Snippet;
	}
	let { left, right, children }: Props = $props();

	let isLeftHover = $state(false);
</script>

<!-- {#snippet sum(a: number, b: number)}
	<span>{a} + {b} = {@render bold(a + b)}</span>
{/snippet}

{#snippet bold(x: any)}
	<b>{x}</b>
{/snippet} -->

<div class="div-test">
	{isLeftHover}
</div>

<div>
	<button>
		{#if left}
			<div
				role="presentation"
				class="left-content"
				onmouseenter={() => {
					isLeftHover = true;
				}}
				onmouseleave={() => {
					isLeftHover = false;
				}}
			>
				{@render left()}
			</div>
		{/if}

		{@render children()}

		{#if right}
			<div class="right-content">
				{@render right()}
			</div>
		{/if}
	</button>
</div>

<style>
	button {
		border: none;
		background-color: grey;
		color: aliceblue;
		padding: 0 20px;
		height: 45px;
		font-weight: bold;
		border-radius: 5px;
		cursor: pointer;
		display: flex;
		align-items: center;
		justify-content: center;
		.left-content {
			margin-inline-end: 10px;
		}
		.right-content {
			margin-inline-start: 10px;
		}
	}
	.div-test {
		background-color: white;
		height: 30px;
		width: 60px;
		pad: 0 20px;
		border-radius: 5px;
		margin-inline-end: 10x;
	}
</style>

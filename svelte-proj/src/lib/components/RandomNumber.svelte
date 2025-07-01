<script lang="ts">
	import { untrack } from 'svelte';

	let randomNumber = $state(Math.floor(Math.random() * 10));
	let doubleRandomNumber = $derived(randomNumber * 2);
	let staleDoubleRandomNumber = $state();
	let history: number[] = $state([]);
	let badExampleHistory: number[] = $state([]);

	let historyPtag: HTMLParagraphElement;
	$effect(() => {
		// this will be stale as value won't be undapted syncrhonously
		// state updating is offloaded to macrotask queue
		staleDoubleRandomNumber = randomNumber * 2;

		// can cause infinite loop
		// history.push(randomNumber);

		// untrack prevents infinite loop due to state keep being updated
		// but this means that history will only be updated when the component
		// mounts to the DOM
		untrack(() => {
			// unelss we do this wtf
			randomNumber;
			badExampleHistory.push(randomNumber);
		});
	});
</script>

<div>
	<h2>The random number is: {randomNumber}</h2>
	<h2>Double random number is: {doubleRandomNumber}</h2>
	<p bind:this={historyPtag}>History: {history}</p>

	<button
		onclick={() => {
			randomNumber = Math.floor(Math.random() * 10);
			// this is better, you don't need $effect for this
			history.push(randomNumber);
			console.log({ randomNumber, doubleRandomNumber, staleDoubleRandomNumber });
		}}>Generate</button
	>
</div>

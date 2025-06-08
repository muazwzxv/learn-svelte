<script lang="ts">
	let randomNumber = $state(Math.floor(Math.random() * 10));
	let doubleRandomNumber = $derived(randomNumber * 2);
	let staleDoubleRandomNumber = $state();
	$effect(() => {
		// this will be stale as value won't be undapted syncrhonously
		// state updating is offloaded to macrotask queue
		staleDoubleRandomNumber = randomNumber * 2;
	});
</script>

<div>
	<h2>The random number is: {randomNumber}</h2>
	<h2>Double random number is: {doubleRandomNumber}</h2>

	<button
		onclick={() => {
			randomNumber = Math.floor(Math.random() * 10);
			console.log({ randomNumber, doubleRandomNumber, staleDoubleRandomNumber });
		}}>Generate</button
	>
</div>

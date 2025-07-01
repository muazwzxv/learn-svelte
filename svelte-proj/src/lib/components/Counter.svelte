<script lang="ts">
	let count = $state(0);
	let frequency = $state(1000);
	let isPaused = $state(false);

	$effect(() => {
		let interval: ReturnType<typeof setInterval>;
		if (!isPaused) {
			interval = setInterval(() => {
				count += 1;
			}, frequency);
		}

		return () => {
			clearInterval(interval);
		};
	});
</script>

<div>
	<h1>{count}</h1>

	<button
		onclick={() => {
			frequency *= 2;
		}}>slower</button
	>

	<button
		onclick={() => {
			frequency /= 2;
		}}>faster</button
	>

	<button
		onclick={() => {
			isPaused = !isPaused;
		}}>{isPaused ? 'play' : 'paused'}</button
	>

	<button
		onclick={() => {
			count = 0;
			frequency = 1000; // back to default
		}}>reset</button
	>
</div>

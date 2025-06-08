<script lang="ts">
	let firstName = $state('Muaz');
	let lastName = $state('Wazir');
	let fullName = $derived(`${firstName} ${lastName}`);
	let fullNameUsingDerivedBy = $derived.by(() => {
		// derived by function should not produce side effects (Pure functions)
		return `${firstName} ${lastName}`;
	});
	let userName = $state('bigDihhMuaz');

	let src = 'https://picsum.photos/250/300';
	let bio = 'Hello, <b> Your mom choking on my dihh </b>';

	$effect(() => {
		if (userName || fullName) {
			console.log('User has a username or a full name');
		}
	});
</script>

<div>
	<img {src} alt="A photo of {fullName}" />
	<h1>Hello {userName || fullName}</h1>
	<input
		placeholder="First version of binding input to state"
		value={userName}
		oninput={(e) => {
			// logic executed upon event fired
			userName = e.currentTarget.value;
		}}
	/>
	<input placeholder="Second version of binding input to state" bind:value={userName} />
	<input bind:value={firstName} />
	<input bind:value={lastName} />

	<button
		onclick={() => {
			console.log(fullName); // only gets triggered when we're using the value, then signal event gets triggered and this derived state will be part of the dependency
		}}>Get Full name</button
	>
	<!-- Bro got to trust the html -->
	<p>{@html bio}</p>
</div>

<style>
	h1 {
		color: red;
	}
</style>

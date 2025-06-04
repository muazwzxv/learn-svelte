<script lang="ts">
	let firstName = $state('Muaz');
	let lastName = $state('Wazir');
	let fullName = $derived(`${firstName} ${lastName}`);
	let userName = $state('bigDihhMuaz');

	let src = 'https://picsum.photos/250/300';
	let bio = 'Hello, <b> Your mom choking on my dihh </b>';

	$effect(() => {
		if (userName || fullName) {
			console.log('User has a username or a full name');
		}
	});
</script>

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

<!-- Bro got to trust the html -->
<p>{@html bio}</p>

<style>
	h1 {
		color: red;
	}
</style>

<script lang="ts">
	let name = 'World';
	let src = 'https://picsum.photos/250/300';
	let bio = 'Hello, <b> Your mom choking on my dihh </b>';
</script>

<img {src} alt="A photo of {name}" />
<h1>Hello {name.toUpperCase()}</h1>

<!-- Bro got to trust the html -->
<p>{@html bio}</p>

<style>
	h1 {
		color: red;
	}
</style>

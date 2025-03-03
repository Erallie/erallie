<script lang="ts">
	let { children } = $props();
</script>

<section id="banner">
	{@render children()}
</section>

<style>
	section {
		text-align: right;
		height: 200px;
		display: flex;
		justify-content: center;
		background-image: url("/code-background-7.jpg");
		/* background-attachment: fixed; */
		background-size: cover; /* Cover the entire viewport */
		background-position: top; /* Center the image */
		background-repeat: no-repeat; /* Do not repeat the image */
		/* text-shadow: 0 0 1em black; */
	}
</style>

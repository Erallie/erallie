<script lang="ts">
	import Banner from "./Banner.svelte";
</script>

<Banner>
	<hgroup>
		<h1>We make stuff.</h1>
		<h1><strong>LOTS</strong> of stuff.</h1>
	</hgroup>
</Banner>
<section>
	<h1>What we do</h1>
	<hr />
	<p>
		We code a wide variety of tools, ranging from Discord Bots to Obsidian
		plugins to VR aids. Our areas of focus expand as we are involved in new
		online interests. We aim to make our projects free for all to use.
	</p>
</section>

<style>
	section {
		background-color: rgba(0, 0, 0, 0.2);
		border-radius: 40px;
		margin: 40px auto;
		width: 500px;
		padding: 40px;
	}
	hr {
		width: 100px;
		margin: 1em 0px;
		margin-left: 2px;
		padding: 0px;
	}
</style>

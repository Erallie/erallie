<script lang="ts">
	import Button from "$lib/components/Button.svelte";
	import Banner from "./Banner.svelte";
</script>

<Banner>
	<hgroup>
		<h1>We make stuff.</h1>
		<h1><strong>LOTS</strong> of stuff.</h1>
	</hgroup>
</Banner>
<section id="about">
	<h1>Who we are</h1>
	<hr />
	<p>
		We are a branch of <a href="https://gozarproductions.com"
			>Gozar Productions</a>
		that makes tools to aid in the use of various programs. If there's something
		we think a program should do, and we see the functionality doesn't exist,
		we make it. And then we share it for others to use too.
	</p>
</section>
<section id="our-projects">
	<img src="/code-background-7.jpg" alt="code-background" />
	<div>
		<h1>Our Projects</h1>
		<hr />
		<p>
			Our tools range from Discord Bots to Obsidian plugins to VR aids. We
			make more stuff as we get involved in more stuff. And then we make
			that stuff free for anyone to use.
		</p>
		<Button link="/projects" marginBottomMultiplier={0}
			>View our Projects</Button>
	</div>
</section>

<style>
	section#about {
		background-color: rgba(0, 0, 0, 0.2);
		border-radius: 40px;
		margin: 40px auto;
		width: 500px;
		padding: 40px;
	}
	section#our-projects {
		width: 100%;
		display: flex;
		justify-content: left;
		background-color: black;
		height: min-content;
		& > img {
			z-index: 0;
			min-height: 100%;
			width: auto;
			height: auto;
			max-width: 45%;
			max-height: none;
			mask-image: linear-gradient(-70deg, transparent 20%, black 20%);
			mask-size: 100% 100%;
			--webkit-mask-size: 100% 100%;
			object-fit: cover;
		}
		& > div {
			width: 400px;
			max-width: 60%;
			margin: auto;
			margin-left: 50px;
			padding: 40px 0;
		}
	}
	hr {
		width: 100px;
		margin: 1em 0px;
		margin-left: 2px;
		padding: 0px;
	}
</style>

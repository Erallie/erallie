<script lang="ts">
	import { type ButtonProps } from "$lib/types/types";
	let {
		link,
		newTab,
		customSVG,
		marginTopMultiplier,
		marginBottomMultiplier,
		children,
	}: ButtonProps = $props();

	// Function to determine if the link is absolute
	/* function isAbsoluteUrl(url: string) {
        return /^(http|https):\/\//.test(url) || url.startsWith("www");
    } */
</script>

<a
	href={link}
	target={newTab ? "_blank" : undefined}
	style="text-decoration: none;">
	<button
		style="--margin-top-multiplier: {marginTopMultiplier !== undefined
			? `${marginTopMultiplier}`
			: '1'}; --margin-bottom-multiplier: {marginBottomMultiplier !==
		undefined
			? `${marginBottomMultiplier}`
			: '1'}">
		{@render children()}
		{#if !customSVG}
			<svg
				xmlns="http://www.w3.org/2000/svg"
				width="200"
				height="60"
				viewBox="0 0 200 60">
				<g
					stroke="currentColor"
					stroke-width="5"
					stroke-linecap="round">
					<line x1="2.5" y1="30" x2="197.5" y2="30 " />
					<line x1="197.5" y1="30" x2="160" y2="2.5" />
					<line x1="197.5" y1="30" x2="160" y2="57.5" />
				</g>
			</svg>
		{/if}
	</button>
</a>

<style>
	button {
		--text-color: 255, 255, 255;
		display: inline-flex; /* Use flexbox for horizontal alignment */
		align-items: center; /* Center items vertically */
		font-family: Montserrat;
		color: rgb(var(--text-color));
		border-radius: 50px;
		padding: 16px 28px;
		border: 2px solid rgb(var(--text-color));
		background-color: rgba(var(--text-color), 0);
		text-align: center;
		letter-spacing: 0.25em;
		text-transform: uppercase;
		font-size: 0.95rem;
		margin: calc(20px * var(--margin-top-multiplier)) auto
			calc(20px * var(--margin-bottom-multiplier));
		transition:
			background-color 0.3s,
			color 1s,
			border-color 1s;

		& > svg {
			width: auto;
			/* aspect-ratio: 200 / 60; */
			height: 0.8em;
			vertical-align: middle; /* This can be removed with flexbox */
			transform: translate(0, -1px);
			padding-left: 0.5em;
			transition: height 0.3s;
		}
		&:hover {
			background-color: rgba(var(--text-color), 0.15);
			& > svg {
				height: 1em;
			}
		}
	}
</style>

<script lang="ts">
	import { onMount } from "svelte";
	import { marked } from "marked";
	let { repo, branch } = $props();

	let markdownContent: string = $state("");
	let htmlContent: string = $state("");

	// Function to transform heading text into a valid ID
	function transformToId(text: string): string {
		return text
			.toLowerCase() // Convert to lowercase
			.replace(" ", "-") // Replace non-alphanumeric characters with hyphens
			.replace(/[\'\/]/, ""); // Remove leading and trailing hyphens
	}

	onMount(async () => {
		try {
			const response = await fetch(
				`https://raw.githubusercontent.com/Erallie/${repo}/refs/heads/${branch}/README.md`
			);
			if (!response.ok) {
				throw new Error("Network response was not ok");
			}
			markdownContent = await response.text();
			htmlContent = marked(markdownContent) as string; // This should be a string
			console.log(htmlContent);

			// Regex patterns for <h1> and <h2>
			const h1Regex = /(<h1>((?:(?!<\/h1>).)+)(?:(?!(?:\n)?<h1>).)+)/gms;
			const h2Regex =
				/(<h2>((?:(?!<\/h2>).)+)(?:(?!(?:\n)?(?:(?:<h2>)|(?:<\/section>))).)+)/gms;
			const h3Regex =
				/(<h3>((?:(?!<\/h3>).)+)(?:(?!(?:\n)?(?:(?:<h3>)|(?:<\/section>))).)+)/gms;
			const h4Regex =
				/(<h4>((?:(?!<\/h4>).)+)(?:(?!(?:\n)?(?:(?:<h4>)|(?:<\/section>))).)+)/gms;

			// Replace <h1> tags with <section> tags using exec
			let match;

			function addSection(match: RegExpExecArray) {
				const fullMatch = match[0]; // The entire <h2>...</h2> match
				const content = match[1]; // The content inside the <h2> tags
				const id = transformToId(match[2]); // Transform the content to create an ID
				htmlContent = htmlContent.replace(
					fullMatch,
					`<section id="${id}" class="readme-section">${content}</section>`
				);
			}
			while ((match = h1Regex.exec(htmlContent)) !== null) {
				addSection(match);
			}
			while ((match = h2Regex.exec(htmlContent)) !== null) {
				addSection(match);
			}
			while ((match = h3Regex.exec(htmlContent)) !== null) {
				addSection(match);
			}
			while ((match = h4Regex.exec(htmlContent)) !== null) {
				addSection(match);
			}

			console.log(htmlContent);

			// Add horizontal rules after headers
			htmlContent = htmlContent
				.replaceAll(/(<h[1234]>.*?<\/h[1234]>)/gms, `$1\n<hr />`)
				.replaceAll(
					/(<a href=\"(?!#)(?:(?!\").)+\")(>(?:(?!<).)+<\/a>)/gms,
					`$1 target="_blank"$2`
				);
		} catch (error) {
			console.error("Error fetching markdown:", error);
		}
	});
</script>

<div class="markdown">
	{@html htmlContent}
</div>

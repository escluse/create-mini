<script>
	import "../app.css";

	let { children } = $props();
</script>

<div class="core">
	<main class="core__content">
		{@render children()}
	</main>
</div>

<style>
	.core {
		display: grid;
		width: 100%;
		height: 100vh;
		grid-template-areas: ". content .";
		grid-template-columns: 1fr minmax(auto, 450px) 1fr;
	}

	.core__content {
		grid-area: content;
		align-content: center;
	}
</style>

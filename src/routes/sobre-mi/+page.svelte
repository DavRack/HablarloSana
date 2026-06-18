<script lang="ts">
	import { aboutMe } from '$lib/config';
</script>

<svelte:head>
	<title>Sobre Mí - HablarloSana</title>
</svelte:head>

<!-- ponytail: copied structure from FAQ, using simple semantic HTML -->
<main class="about-page">
	<div class="container">
		<h1>Sobre Mí</h1>
		<a href="/landingpage" class="back-link">← Volver al inicio</a>
		
		<div class="content">
			{#each aboutMe as paragraph}
				<p>{paragraph}</p>
			{/each}
		</div>
	</div>
</main>

<style>
	.about-page { 
		padding: 40px 20px; 
		min-height: 100vh;
	}
	.container {
		max-width: 600px; 
		margin: 0 auto; 
	}
	h1 {
		color: var(--color-primary, #333);
		margin-bottom: 1rem;
	}
	.back-link {
		display: inline-block;
		margin-bottom: 2rem;
		text-decoration: none;
		color: var(--color-text-muted, #666);
	}
	.back-link:hover {
		text-decoration: underline;
	}
	.content {
		background: rgba(255, 255, 255, 0.7);
		border: 1px solid rgba(255, 255, 255, 0.4); 
		border-radius: 12px;
		padding: 2rem;
		box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
		backdrop-filter: blur(10px);
		-webkit-backdrop-filter: blur(10px);
	}
	p { 
		margin-bottom: 1rem; 
		color: var(--color-text-muted, #666);
		line-height: 1.6;
	}
	p:last-child {
		margin-bottom: 0;
	}
</style>

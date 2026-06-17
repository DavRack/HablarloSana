<script lang="ts">
	import { faq } from '$lib/config';
</script>

<svelte:head>
	<title>Preguntas Frecuentes - HablarloSana</title>
</svelte:head>

<main class="faq-page">
	<div class="container">
		<h1>Preguntas Frecuentes</h1>
		<a href="/landingpage" class="back-link">← Volver al inicio</a>
		
		<div class="faq-list">
			<!-- ponytail: using native details/summary for zero-js accordion -->
			{#each faq as item}
				<details>
					<summary>{item.question}</summary>
					<p>{item.answer}</p>
				</details>
			{/each}
		</div>
	</div>
</main>

<style>
	.faq-page { 
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
	details { 
		margin-bottom: 1rem; 
		padding: 1rem; 
		background: rgba(255, 255, 255, 0.5);
		border: 1px solid rgba(145, 162, 186, 0.4); 
		border-radius: 8px; 
	}
	summary { 
		cursor: pointer; 
		font-weight: 600; 
		color: var(--color-text, #333);
	}
	p { 
		margin-top: 0.8rem; 
		color: var(--color-text-muted, #666);
		line-height: 1.5;
	}
</style>

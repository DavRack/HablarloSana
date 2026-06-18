<script lang="ts">
	import { faq } from '$lib/config';

	// Array to track open state of each item independently
	let openState: boolean[] = $state(faq.map(() => false));
</script>

<svelte:head>
	<title>Preguntas Frecuentes - HablarloSana</title>
</svelte:head>

<main class="faq-page">
	<div class="container">
		<h1>Preguntas Frecuentes</h1>
		<a href="/landingpage" class="back-link">← Volver al inicio</a>
		
		<div class="faq-list">
			{#each faq as item, i}
				<div class="faq-item" class:is-open={openState[i]}>
					<button class="faq-summary" on:click={() => openState[i] = !openState[i]}>
						<span>{item.question}</span>
						<span class="toggle-icon">
							<svg viewBox="0 0 24 24" class="chevron" class:rotated={openState[i]}>
								<path d="M7 10l5 5 5-5z" fill="currentColor"/>
							</svg>
						</span>
					</button>
					<div class="faq-content-wrapper" class:is-open={openState[i]}>
						<div class="faq-content">
							<p>{item.answer}</p>
						</div>
					</div>
				</div>
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
	.faq-item { 
		margin-bottom: 1rem; 
		padding: 1.25rem; 
		background: rgba(255, 255, 255, 0.9);
		border: 1px solid rgba(255, 255, 255, 0.4); 
		border-radius: 12px; 
		box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
		transition: transform 0.3s ease, box-shadow 0.3s ease, border-color 0.3s ease;
		position: relative;
	}
	.faq-item::before {
		content: '';
		position: absolute;
		top: 0;
		left: 0;
		width: 4px;
		height: 100%;
		background: var(--color-primary);
		opacity: 0.7;
		transition: opacity 0.3s ease;
	}
	.faq-item:hover {
		transform: translateY(-4px);
		box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
		border-color: rgba(255, 255, 255, 0.8);
	}
	.faq-item:hover::before {
		opacity: 1;
	}
	.faq-item.is-open {
		border-color: rgba(255, 255, 255, 0.9);
		box-shadow: 0 8px 16px rgba(0, 0, 0, 0.08);
	}
	.faq-summary { 
		width: 100%;
		background: none;
		border: none;
		padding: 0;
		margin: 0;
		display: flex;
		justify-content: space-between;
		align-items: center;
		cursor: pointer; 
		font-family: inherit;
		font-size: 1rem;
		font-weight: 600; 
		color: var(--color-text, #333);
		text-align: left;
	}
	.toggle-icon {
		display: flex;
		align-items: center;
		justify-content: center;
		width: 24px;
		height: 24px;
		flex-shrink: 0;
		color: var(--color-primary);
	}
	.chevron {
		width: 24px;
		height: 24px;
		transition: transform 0.3s ease;
	}
	.chevron.rotated {
		transform: rotate(180deg);
	}
	.faq-content-wrapper {
		display: grid;
		grid-template-rows: 0fr;
		transition: grid-template-rows 0.3s ease-out;
	}
	.faq-content-wrapper.is-open {
		grid-template-rows: 1fr;
	}
	.faq-content {
		overflow: hidden;
	}
	p { 
		margin-top: 0.8rem; 
		margin-bottom: 0;
		color: var(--color-text-muted, #666);
		line-height: 1.5;
	}
</style>

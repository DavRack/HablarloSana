<script lang="ts">
	import { testimonials } from '$lib/config';
</script>

<svelte:head>
	<title>Experiencias - HablarloSana</title>
</svelte:head>

<!-- ponytail: copied structure from FAQ/Sobre Mí. Using basic cards for testimonials. -->
<main class="testimonials-page">
	<div class="container">
		<h1>Experiencias</h1>
		<a href="/landingpage" class="back-link">← Volver al inicio</a>
		
		<div class="testimonials-list">
			{#each testimonials as exp}
				<div class="testimonial-card">
					<p class="quote">"{exp.quote}"</p>
					<p class="author">- {exp.author}</p>
				</div>
			{/each}
		</div>
	</div>
</main>

<style>
	.testimonials-page { 
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
	.testimonials-list {
		display: flex;
		flex-direction: column;
		gap: 1.5rem;
	}
	.testimonial-card {
		background: rgba(255, 255, 255, 0.7);
		border: 1px solid rgba(255, 255, 255, 0.4); 
		border-radius: 12px;
		padding: 1.5rem;
		box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
		backdrop-filter: blur(10px);
		-webkit-backdrop-filter: blur(10px);
		transition: transform 0.3s ease, box-shadow 0.3s ease, border-color 0.3s ease;
		position: relative;
		overflow: hidden;
	}
	.testimonial-card::before {
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
	.testimonial-card:hover {
		transform: translateY(-4px);
		box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
		border-color: rgba(255, 255, 255, 0.8);
	}
	.testimonial-card:hover::before {
		opacity: 1;
	}
	.quote { 
		font-style: italic;
		color: var(--color-text, #333);
		margin-bottom: 1rem;
		line-height: 1.5;
	}
	.author {
		font-weight: 600;
		color: var(--color-text-muted, #666);
		text-align: right;
		font-size: 0.9rem;
	}
</style>

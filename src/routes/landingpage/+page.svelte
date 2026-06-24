<script lang="ts">
	import { contactInfo } from '$lib/config';

	async function handleShare() {
		try {
			if (navigator.share) {
				await navigator.share({
					title: 'HablarloSana - Psicología',
					url: window.location.href
				});
			} else if (navigator.clipboard && navigator.clipboard.writeText) {
				await navigator.clipboard.writeText(window.location.href);
				alert('Enlace copiado al portapapeles');
			} else {
				const textArea = document.createElement("textarea");
				textArea.value = window.location.href;
				document.body.appendChild(textArea);
				textArea.select();
				document.execCommand("copy");
				textArea.remove();
				alert('Enlace copiado al portapapeles');
			}
		} catch (err) {
			console.error('Share failed:', err);
		}
	}
</script>

<svelte:head>
	<title>HablarloSana - Psicología</title>
</svelte:head>

<main class="landing-page">
	<button class="share-btn glass-panel" on:click={handleShare} aria-label="Compartir">
		<svg viewBox="0 0 24 24" fill="currentColor" height="20" width="20">
			<path d="M18 16.08c-.76 0-1.44.3-1.96.77L8.91 12.7c.05-.23.09-.46.09-.7s-.04-.47-.09-.7l7.05-4.11c.54.5 1.25.81 2.04.81 1.66 0 3-1.34 3-3s-1.34-3-3-3-3 1.34-3 3c0 .24.04.47.09.7L8.04 9.81C7.5 9.31 6.79 9 6 9c-1.66 0-3 1.34-3 3s1.34 3 3 3c.79 0 1.5-.31 2.04-.81l7.12 4.16c-.05.21-.08.43-.08.65 0 1.61 1.31 2.92 2.92 2.92 1.61 0 2.92-1.31 2.92-2.92s-1.31-2.92-2.92-2.92z"/>
		</svg>
	</button>

	<div class="container content">
		<header class="header">
			<img class="logo" src="/logo.png" alt="Hablarlo Sana" />
		</header>

		<section class="links-section">
			<!-- Social Icons -->
			<div class="social-icons">
				<a
					href={contactInfo.instagram.link}
					target="_blank"
					rel="noopener noreferrer"
					class="social-icon instagram-icon"
					aria-label="Instagram"
				>
					<svg viewBox="0 0 24 24" fill="currentColor" height="24" width="24">
						<path
							d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zM12 0C8.741 0 8.333.014 7.053.072 2.695.272.273 2.69.073 7.052.014 8.333 0 8.741 0 12c0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98C8.333 23.986 8.741 24 12 24c3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98C15.668.014 15.259 0 12 0zm0 5.838a6.162 6.162 0 100 12.324 6.162 6.162 0 000-12.324zM12 16a4 4 0 110-8 4 4 0 010 8zm6.406-11.845a1.44 1.44 0 100 2.881 1.44 1.44 0 000-2.881z"
						/>
					</svg>
				</a>

				<a
					href={contactInfo.tiktok.link}
					target="_blank"
					rel="noopener noreferrer"
					class="social-icon tiktok-icon"
					aria-label="TikTok"
				>
					<svg viewBox="0 0 24 24" fill="currentColor" height="24" width="24">
						<path
							d="M19.59 6.69a4.83 4.83 0 0 1-3.77-4.25V2h-3.45v13.67a2.89 2.89 0 0 1-5.2 1.74 2.89 2.89 0 0 1 2.31-4.64 2.93 2.93 0 0 1 .88.13V9.4a6.84 6.84 0 0 0-1-.05A6.33 6.33 0 0 0 5 20.1a6.34 6.34 0 0 0 10.86-4.43v-7a8.16 8.16 0 0 0 4.77 1.52v-3.4a4.85 4.85 0 0 1-1-.1z"
						/>
					</svg>
				</a>

				<a href="mailto:{contactInfo.email.address}" class="social-icon email-icon" aria-label="Email">
					<svg viewBox="0 0 24 24" fill="currentColor" height="24" width="24">
						<path
							d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"
						/>
					</svg>
				</a>
			</div>

			<!-- WhatsApp / Reserva tu cita -->
			<a
				href="https://wa.me/{contactInfo.whatsapp.phoneNumber}?text={encodeURIComponent(
					contactInfo.whatsapp.message
				)}"
				target="_blank"
				rel="noopener noreferrer"
				class="link-card primary-card glass-panel"
			>
				<div class="card-content">
					<div class="icon whatsapp-icon">
						<svg viewBox="0 0 24 24" fill="currentColor" height="24" width="24">
							<path
								d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51a12.8 12.8 0 0 0-.57-.01c-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 0 1-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 0 1-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 0 1 2.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0 0 12.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 0 0 5.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 0 0-3.48-8.413Z"
							/>
						</svg>
					</div>
					<div class="text">
						<h3>Reserva tu cita</h3>
					</div>
				</div>
			</a>

			<!-- FAQ -->
			<!-- ponytail: reused existing card component, standard link to zero-js route -->
			<a href="/FAQ" data-sveltekit-preload-code="eager" class="link-card glass-panel">
				<div class="card-content">
					<div class="icon faq-icon">
						<svg viewBox="0 0 24 24" fill="currentColor" height="24" width="24">
							<path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm1 17h-2v-2h2v2zm2.07-7.75l-.9.92C13.45 12.9 13 13.5 13 15h-2v-.5c0-1.1.45-2.1 1.17-2.83l1.24-1.26c.37-.36.59-.86.59-1.41 0-1.1-.9-2-2-2s-2 .9-2 2H8c0-2.21 1.79-4 4-4s4 1.79 4 4c0 .88-.36 1.68-.93 2.25z"/>
						</svg>
					</div>
					<div class="text">
						<h3>Preguntas Frecuentes</h3>
					</div>
				</div>
			</a>

			<!-- Sobre Mí -->
			<a href="/sobre-mi" data-sveltekit-preload-code="eager" class="link-card glass-panel">
				<div class="card-content">
					<div class="icon about-icon">
						<svg viewBox="0 0 24 24" fill="currentColor" height="24" width="24">
							<path d="M12 12c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm0 2c-2.67 0-8 1.34-8 4v2h16v-2c0-2.66-5.33-4-8-4z"/>
						</svg>
					</div>
					<div class="text">
						<h3>Sobre Mí</h3>
					</div>
				</div>
			</a>

			<!-- Experiencias -->
			<a href="/experiencias" data-sveltekit-preload-code="eager" class="link-card glass-panel">
				<div class="card-content">
					<div class="icon experiences-icon">
						<svg viewBox="0 0 24 24" fill="currentColor" height="24" width="24">
							<path d="M21 6h-2v9H6v2c0 .55.45 1 1 1h11l4 4V7c0-.55-.45-1-1-1zm-4 6V3c0-.55-.45-1-1-1H3c-.55 0-1 .45-1 1v14l4-4h10c.55 0 1-.45 1-1z"/>
						</svg>
					</div>
					<div class="text">
						<h3>Cuando hablarlo sana</h3>
					</div>
				</div>
			</a>

			<!-- Staff Supervisión Clínica -->
			<a href="https://docs.google.com/forms/d/e/1FAIpQLSe8dYgoG52hxcIgYnhu5FCeK_MkOfzgS1jiBqLykZYCwaRbHw/viewform?usp=preview" target="_blank" rel="noopener noreferrer" class="link-card glass-panel">
				<div class="card-content">
					<div class="icon staff-icon">
						<svg viewBox="0 0 24 24" fill="currentColor" height="24" width="24">
							<path d="M16 11c1.66 0 2.99-1.34 2.99-3S17.66 5 16 5c-1.66 0-3 1.34-3 3s1.34 3 3 3zm-8 0c1.66 0 2.99-1.34 2.99-3S9.66 5 8 5C6.34 5 5 6.34 5 8s1.34 3 3 3zm0 2c-2.33 0-7 1.17-7 3.5V19h14v-2.5c0-2.33-4.67-3.5-7-3.5zm8 0c-.29 0-.62.02-.97.05 1.16.84 1.97 1.97 1.97 3.45V19h6v-2.5c0-2.33-4.67-3.5-7-3.5z"/>
						</svg>
					</div>
					<div class="text">
						<h3>Únete al equipo de Supervisión Clínica</h3>
					</div>
				</div>
			</a>

		</section>
	</div>
</main>

<style>
	.landing-page {
		position: relative;
		min-height: 100vh;
		display: flex;
		align-items: center;
		justify-content: center;
		padding: 40px 0;
		overflow: hidden;
	}

	.share-btn {
		position: absolute;
		top: 2em;
		right: 2em;
		width: 44px;
		height: 44px;
		border-radius: var(--radius-full);
		border: none;
		display: flex;
		align-items: center;
		justify-content: center;
		color: var(--color-primary);
		cursor: pointer;
		z-index: 10;
		transition: transform 0.2s ease;
		padding: 0;
	}

	.share-btn:hover {
		transform: scale(1.05);
	}

	.content {
		position: relative;
		z-index: 1;
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 0px;
	}

	.header {
		text-align: center;
		max-width: 500px;
		animation: fadeInDown 0.8s ease-out;
	}

	@keyframes fadeInDown {
		from {
			opacity: 0;
			transform: translateY(-20px);
		}
		to {
			opacity: 1;
			transform: translateY(0);
		}
	}

	.logo {
		display: block;
		width: clamp(220px, 55vw, 350px);
		height: auto;
	}

	.subtitle {
		font-size: 1.1rem;
		color: var(--color-text-muted);
		line-height: 1.6;
		margin: 0;
	}

	.links-section {
		display: flex;
		flex-direction: column;
		gap: 16px;
		width: 100%;
		max-width: 400px;
		animation: fadeInUp 0.8s ease-out 0.2s both;
	}

	@keyframes fadeInUp {
		from {
			opacity: 0;
			transform: translateY(20px);
		}
		to {
			opacity: 1;
			transform: translateY(0);
		}
	}

	.link-card {
		display: block;
		transition: var(--transition);
		position: relative;
		overflow: hidden;
	}

	.link-card::before {
		content: '';
		position: absolute;
		top: 0;
		left: 0;
		width: 4px;
		height: 100%;
		background: transparent;
		transition: var(--transition);
	}

	.link-card:hover {
		transform: translateY(-4px);
		box-shadow: var(--shadow-hover);
		border-color: rgba(255, 255, 255, 0.8);
	}

	.link-card:hover::before {
		background: var(--color-primary);
	}

	.primary-card {
		border: 1px solid rgba(145, 162, 186, 0.4); /* Cool Steel border */
		background: rgba(255, 255, 255, 0.85);
	}

	.primary-card:hover::before {
		background: #25d366; /* WhatsApp brand color */
	}

	.card-content {
		display: flex;
		align-items: center;
		padding: 20px 24px;
		gap: 20px;
	}

	.icon {
		display: flex;
		align-items: center;
		justify-content: center;
		width: 52px;
		height: 52px;
		border-radius: var(--radius-full);
		background: var(--color-bg);
		color: var(--color-primary);
		transition: var(--transition);
		flex-shrink: 0;
	}

	.primary-card .icon {
		background: #25d366;
		color: white;
		box-shadow: 0 4px 12px rgba(37, 211, 102, 0.3);
	}

	.social-icons {
		display: flex;
		justify-content: center;
		gap: 16px;
		margin-bottom: 8px;
	}

	.social-icon {
		display: flex;
		align-items: center;
		justify-content: center;
		width: 52px;
		height: 52px;
		border-radius: var(--radius-full);
		background: rgba(255, 255, 255, 0.85);
		color: var(--color-primary);
		transition: transform 0.3s ease, box-shadow 0.3s ease, background 0.3s ease, color 0.3s ease;
		box-shadow: 0 4px 6px rgba(0,0,0,0.05);
	}

	.social-icon:hover {
		transform: translateY(-4px);
	}

	.social-icon.instagram-icon {
		background: linear-gradient(
			45deg,
			#f09433 0%,
			#e6683c 25%,
			#dc2743 50%,
			#cc2366 75%,
			#bc1888 100%
		);
		color: white;
		box-shadow: 0 4px 12px rgba(220, 39, 67, 0.3);
	}

	.link-card:hover .icon.faq-icon {
		background: var(--color-primary);
		color: white;
		box-shadow: 0 4px 12px rgba(20, 93, 160, 0.3);
	}

	.link-card:hover .icon.about-icon {
		background: var(--color-primary);
		color: white;
		box-shadow: 0 4px 12px rgba(20, 93, 160, 0.3);
	}

	.link-card:hover .icon.experiences-icon {
		background: var(--color-primary);
		color: white;
		box-shadow: 0 4px 12px rgba(20, 93, 160, 0.3);
	}

	.link-card:hover .icon.staff-icon {
		background: var(--color-primary);
		color: white;
		box-shadow: 0 4px 12px rgba(20, 93, 160, 0.3);
	}

	.social-icon.tiktok-icon {
		background: #000000;
		color: white;
		box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
	}

	.social-icon.email-icon {
		background: #ea4335;
		color: white;
		box-shadow: 0 4px 12px rgba(234, 67, 53, 0.3);
	}

	.text h3 {
		font-size: 1.15rem;
		margin-bottom: 4px;
		color: var(--color-text);
		transition: var(--transition);
	}

	.primary-card .text h3 {
		color: var(--color-primary);
	}

	.text p {
		font-size: 0.95rem;
		color: var(--color-text-muted);
		margin: 0;
	}

	/* Responsive tweaks */
	@media (min-width: 768px) {
		.landing-page {
			padding: 80px 0;
		}

		.logo {
			font-size: 4rem;
		}

		.subtitle {
			font-size: 1.25rem;
		}

		.links-section {
			gap: 24px;
		}

		.card-content {
			padding: 24px 28px;
		}
	}
</style>

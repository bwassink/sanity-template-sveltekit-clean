<script lang="ts">
	import { isPreviewing, VisualEditing } from '@sanity/visual-editing/svelte';
	import { page } from '$app/stores';
	import LiveMode from '../components/LiveMode.svelte';
	import '../lib/utils/styles.css';
	import Header from '../components/Header.svelte';
	import Footer from '../components/Footer.svelte';
</script>

{#if $isPreviewing}
	<a href={`/preview/disable?redirect=${$page.url.pathname}`} class="preview-toggle">
		<span>Preview Enabled</span>
		<span>Disable Preview</span>
	</a>
{/if}

<!-- <div class="container"> -->
<Header />
<slot />
<Footer />
<!-- </div> -->

{#if $isPreviewing}
	<VisualEditing />
	<LiveMode />
{/if}

<style>
	/* .header {
		display: flex;
		padding: 0 var(--space-1);
		border-bottom: 1px solid #ced2d9;

		z-index: 10;
		background: var(--white);
		position: fixed;
		left: 0;
		right: 0;
		top: 0;
	} */

	/* .header .header__title {
		font-weight: 800;
		font-size: var(--font-size-3);
		line-height: var(--line-height-1);
		padding-left: var(--space-2);
		margin: var(--space-3) 0;
		text-decoration: none;
		color: var(--black);
	}

	.footer {
		display: flex;
		justify-content: flex-end;
		padding: 0 var(--space-3);
	}

	.footer .footer__text {
		font-size: var(--font-size-1);
		line-height: var(--line-height-1);
		display: flex;
		align-items: center;
		gap: 2px;
	} */

	/* @media (min-width: 575px) {
		.container {
			max-width: var(--max-width-1);
			padding: 0 var(--space-4);
		}

		main {
			margin-top: unset;
		}

		.header {
			position: unset;
			border-bottom: none;
			margin: var(--space-3) 0;
			padding: var(--space-2) 0;
			background: unset;
		}

		.header .header__title {
			margin: var(--space-3) 0 var(--space-2);
			font-size: var(--font-size-5);
		}

		.footer {
			margin: var(--space-3) 0;
		}
	} */

	.preview-toggle {
		backdrop-filter: blur(12px);
		border-radius: 0.25rem;
		bottom: 1rem;
		box-shadow:
			0 10px 15px -3px rgba(0, 0, 0, 0.1),
			0 4px 6px -2px rgba(0, 0, 0, 0.05);
		color: #1f2937;
		display: block;
		font-size: 0.75rem;
		font-weight: 500;
		line-height: 1rem;
		padding-bottom: 0.5rem;
		padding-left: 0.75rem;
		padding-right: 0.75rem;
		padding-top: 0.5rem;
		position: fixed;
		right: 1rem;
		text-align: center;
		text-decoration: none;
		z-index: 50;
	}

	.preview-toggle:hover {
		background-color: #ef4444;
		color: #ffffff;
	}

	.preview-toggle span:first-child {
		display: block;
	}
	.preview-toggle:hover span:first-child {
		display: none;
	}

	.preview-toggle span:last-child {
		display: none;
	}
	.preview-toggle:hover span:last-child {
		display: block;
	}
</style>

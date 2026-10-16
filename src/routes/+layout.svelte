<script lang="ts">
	import { page } from '$app/state';
	import { resolve } from '$app/paths';
	import logo from '#lib/assets/rd-tax-solutions-mark.svg';
	import '../app.css';
	import type { LayoutProps } from './$types';

	let { children }: LayoutProps = $props();
	const links = [
		{ href: '/', label: 'Home' },
		{ href: '/about-us', label: 'About Us' },
		{ href: '/what-we-do', label: 'What We Do' },
		{ href: '/sr&ed-explained', label: 'SR&ED Explained' },
		{ href: '/contact-us-1', label: 'Contact Us' }
	] as const;
</script>

<svelte:head>
	<link rel="icon" type="image/svg+xml" href={logo} />
</svelte:head>

<a class="skip-link" href="#main">Skip to content</a>
<div class="utility-bar"><div class="container utility-inner"><span>Expert tax consulting for SR&amp;ED claims in Canada.</span><a href="tel:+19055160005">905 516 0005</a></div></div>
<div class="site">
	<header class="site-header container">
		<a class="brand" href={resolve('/')} aria-label="R&D Tax Solutions home">
			<img src={logo} alt="" width="65" height="65" />
			<span>Tax Solutions<small>SR&amp;ED TAX CONSULTANTS</small></span>
		</a>
		<nav aria-label="Main navigation">
			{#each links as link}
				<a href={resolve(link.href)} aria-current={page.route.id === link.href ? 'page' : undefined}>{link.label}</a>
			{/each}
		</nav>
	</header>

	<main id="main" tabindex="-1" class:home={page.route.id === '/'}>
		{#if page.route.id === '/'}
			{@render children()}
		{:else}
			<div class="container inner-page">
				<p class="breadcrumb"><a href={resolve('/')}>Home</a><span aria-hidden="true">/</span>{links.find(link => link.href === page.route.id)?.label}</p>
				<article>{@render children()}</article>
			</div>
		{/if}
	</main>

	<footer class="site-footer">
		<div class="container footer-main">
			<div><a class="footer-name" href={resolve('/')}>R&amp;D Tax Solutions</a></div>
			<div><h2>Get in touch</h2><a href="tel:+19055160005">905 516 0005</a><a href="mailto:info@rdtaxsolutions.ca">info@rdtaxsolutions.ca</a></div>
			<div><h2>Our office</h2><address>Suite 291, 1235 Fairview Street<br />Burlington, Ontario L7S 2K9</address></div>
		</div>
		<div class="container footer-bottom"><span>© {new Date().getFullYear()} R&amp;D Tax Solutions</span><a href={resolve('/contact-us-1')}>Contact Us <span aria-hidden="true">↗</span></a></div>
	</footer>
</div>

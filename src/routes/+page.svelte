<script lang="ts">
	import { resolve } from '$app/paths';
	import architecture from '#lib/assets/architecture.jpg';
	import ContactForm from '#lib/ContactForm.svelte';
</script>

<svelte:head>
	<title>R&amp;D Tax Solutions</title>
	<meta name="description" content="Expert tax consulting for SR&amp;ED claims in Canada." />
</svelte:head>

<section class="hero" aria-labelledby="hero-title">
	<div class="container hero-grid">
		<div class="hero-copy">
			<h1 id="hero-title">Maximize Your R&amp;D Tax Credits</h1>
			<p class="hero-summary">Expert tax consulting for SR&amp;ED claims in Canada.</p>
			<a class="button button-light" href={resolve('/contact-us-1')}>Get Started Today <span aria-hidden="true">↗</span></a>
		</div>
		<div class="hero-image"><img src={architecture} alt="Glass towers viewed from below in Toronto" width="1200" height="901" fetchpriority="high" /></div>
	</div>
</section>

<section class="container introduction" aria-labelledby="intro-title">
	<div><h2 id="intro-title">About R&amp;D Tax Solutions</h2></div>
	<div><p>At R&amp;D Tax Solutions, we specialize in providing professional consulting services tailored to help clients navigate the complexities of claiming Scientific Research and Development tax credits. Our team of experts is dedicated to maximizing your eligible claims and ensuring compliance with Canadian tax regulations.</p><a class="text-link" href={resolve('/about-us')}>About Us <span aria-hidden="true">↗</span></a></div>
</section>

<section class="home-contact" aria-labelledby="contact-title">
	<div class="container">
		<h2 id="contact-title">Contact Us</h2>
		<div class="contact-grid">
			<ContactForm id="home-contact" />
			<div class="contact-office"><h3>R&amp;D Tax Solutions</h3><address>Suite 291, 1235 Fairview Street<br />Burlington, Ontario L7S 2K9</address><p><a href="tel:+19055160005">1 905 516-0005</a></p></div>
		</div>
	</div>
</section>

# Website

Minimal SvelteKit + TypeScript site, prerendered with `@sveltejs/adapter-static`.

## Development

From this directory:

```sh
nix develop /home/justin/nix-manager#svelte
npm ci
npm run dev
```

`bun run dev` also works from `website/` inside the Svelte Nix shell.
Running it from the parent directory will not find the app's `dev` script.

Edit `src/routes/+page.svelte` for the home page. Add pages as
`src/routes/about/+page.svelte`, for example. Put public assets in `static/`.

## Check and build

```sh
npm run check
npm run build
npm run preview
```

Deploy the contents of `build/` to any static web host. No Node server is
required in production. Pages use directory-style URLs (`/about/index.html`),
so the host only needs standard index-file serving.

For hosting under a subdirectory, configure SvelteKit's `paths.base` in
`vite.config.ts` before building.

## Brand and photography

Global styles are in `src/app.css`. The header uses the supplied
`rd-tax-solutions-mark.svg`; the palette follows its navy and blue tones.

The homepage architectural photograph is by Patrick Tomasso on
[Unsplash](https://unsplash.com/photos/low-angle-photography-curtain-wall-buildings-gMes5dNykus),
used under the [Unsplash License](https://unsplash.com/license).
It is stored locally in `src/lib/assets/architecture.jpg` and is illustrative
stock photography, not a photograph of the firm's office.

## Contact form and content

The shared `src/lib/ContactForm.svelte` appears on Home and Contact Us.
It validates the email address and opens a prepared email to
`info@rdtaxsolutions.ca`. The visitor must send it from their email app;
there is no server-side delivery or submission storage.

Page copy follows the original rdtaxsolutions.ca site, with duplicate sections
removed and minor typo corrections. Its historical program figures and claim
processing estimates have been preserved as requested, not updated.

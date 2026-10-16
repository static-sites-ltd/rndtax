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

For hosting under a subdirectory, set `BASE_PATH` when building, for example
`BASE_PATH=/rndtax npm run build`. It defaults to an empty string for local
development and root-domain hosting.

## GitHub Pages

Push this directory as the root of a GitHub repository (including
`.github/workflows/deploy.yml` and `package-lock.json`). In the repository's
**Settings → Pages → Build and deployment**, select **GitHub Actions** as the
source. Push to `main`, or run **Deploy to GitHub Pages** manually from the
Actions tab, to build and deploy the site.

The workflow installs locked dependencies with Node.js 24, runs the Svelte
checks, builds the site, and deploys `build/`. It reads `BASE_PATH` from GitHub
Pages metadata, supporting repository URLs, user/organization sites, and
custom domains without hardcoding the repository name. Configure any custom
domain in GitHub's Pages settings, then rerun the workflow.

All pages are prerendered with directory-style URLs. A `404.html` fallback
handles unknown routes. No deployment secrets or separate `gh-pages` branch
are required; the workflow uses GitHub's built-in token.

To check a repository-style build locally:

```sh
BASE_PATH=/rndtax npm run build
BASE_PATH=/rndtax npm run preview
```

Open the preview at `/rndtax/`. To return to a root-path build, run
`npm run build` again without `BASE_PATH`.

## Brand and photography

Global styles are in `src/app.css`. The header uses the supplied
`src/lib/assets/rd-tax-solutions-mark.svg`; the palette follows its navy and blue tones.

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

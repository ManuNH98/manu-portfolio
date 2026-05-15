# AGENTS.md

## Project Overview

This repository is a personal portfolio site for Manuel Navarro. It is built as a static Astro site with Tailwind CSS, TypeScript, pnpm, and Vercel deployment.

Primary goals for changes in this repo:

- Keep the site fast, simple, and static-first.
- Preserve the existing dark visual style unless a task explicitly asks for a redesign.
- Improve accessibility, responsiveness, and SEO when touching UI or page structure.
- Make the smallest correct change needed for the task.

## Repository Structure

- `src/pages/` defines Astro routes. `src/pages/index.astro` is the home page.
- `src/layouts/` contains page layouts. `src/layouts/Layout.astro` wraps the main page shell, metadata, navbar, footer, and Vercel Speed Insights.
- `src/components/` contains reusable Astro components such as `Header`, `Navbar`, `Projects`, `Technologies`, `Experience`, `Contact`, and `Footer`.
- `src/styles/` contains global styles. `src/styles/globals.css` is currently minimal/empty.
- `public/` contains static assets copied as-is at build time.
- `public/assets/data/projects.json` stores project card data consumed by `Projects.astro`.
- `public/assets/images/` stores profile, project, and social icon assets.
- `astro.config.mjs` configures Astro, Tailwind via `@tailwindcss/vite`, static output, and the Vercel adapter.
- `tailwind.config.mjs` defines the Tailwind content paths, custom screens, font sizes, and color palette.
- `pnpm-lock.yaml` is the source-of-truth dependency lockfile. Do not use `package-lock.json` or other package-manager lockfiles.

## Commands

Run commands from the repository root.

- `pnpm install` installs dependencies.
- `pnpm run dev` starts the local Astro dev server, usually at `localhost:4321`.
- `pnpm run build` builds the production site.
- `pnpm run preview` previews the production build locally.
- `pnpm run quality:check` runs Astro checks via `astro-check`.
- `pnpm run quality:build` runs the production build.
- `pnpm run quality:gates` runs checks and build together.

Before finishing code changes, prefer running `pnpm run quality:gates`. If that is too expensive or not possible, run the narrowest relevant command and report what was or was not verified.

## Coding Guidelines

- Prefer Astro components for UI. Do not introduce client-side JavaScript or framework islands unless the task requires interactivity.
- Keep components small and colocated in `src/components/` unless a new route or layout is needed.
- Use public asset URLs like `/assets/images/...` for files under `public/`. Avoid importing files from `../../public/...` inside components.
- Use Tailwind utility classes for styling, following the existing dark theme and custom color names from `tailwind.config.mjs`.
- Tailwind is wired through `@tailwindcss/vite` and imported from `src/styles/globals.css`; do not re-add `@astrojs/tailwind`.
- Preserve the Spanish content tone unless the task asks for copy changes or localization.
- Keep TypeScript/Astro frontmatter minimal. Add shared types only when they reduce real duplication or prevent likely mistakes.
- Avoid unnecessary abstractions, new dependencies, or broad refactors.
- Do not add comments unless they clarify non-obvious behavior.

## Tailwind And Design Notes

- The site uses a dark background (`zinc-950`/`#09090B` style) with white text, zinc grays, and yellow accents.
- Custom screens include `microsm`, `sm`, `md`, `lg`, `xl`, `2xl`, and `4xl`.
- Custom font sizes are defined in `tailwind.config.mjs`; use existing scale values where possible.
- When changing layout, verify both mobile and desktop behavior.
- Prefer improving existing visual language over replacing it wholesale.

## Content And Assets

- Project data lives in `public/assets/data/projects.json`.
- Project images should live under `public/assets/images/projects/<project-name>/`.
- Social icons live under `public/assets/images/icons/`.
- Use descriptive `alt` text for meaningful images. Use empty `alt=""` only for decorative images.
- Keep image paths root-relative when referenced from markup or JSON, for example `/assets/images/projects/f1stats/f1stats.webp`.

## Accessibility Guidelines

- Use semantic landmarks and headings in a logical order.
- Interactive elements must be keyboard accessible and have visible focus states.
- Links should have real destinations when possible. Avoid leaving production links as `#` unless the section/target does not exist yet.
- Every meaningful image needs useful `alt` text.
- Preserve sufficient contrast against the dark background.
- When adding navigation links to sections, add matching section IDs.

## SEO Guidelines

- Keep page titles descriptive.
- Add or update meta descriptions when changing page-level content.
- Use semantic sections for major content areas.
- Prefer canonical, stable URLs for public links.
- Do not add structured data unless the task needs it or the page content supports it.

## AI Skills Workflow

This repo may include AI skill instructions under `.agents/skills/`, but `.agents/` is ignored by Git. If those skills are available in the current environment, route work intentionally:

- Astro pages, components, routing, or config: `astro`.
- Tailwind layout and responsive styling: `tailwind-css-patterns`.
- High-fidelity UI polish: `frontend-design`.
- Accessibility audits and fixes: `accessibility`.
- SEO metadata and structured data: `seo`.
- Type-heavy TypeScript work: `typescript-advanced-types`.
- Vercel preview or production deployments: `deploy-to-vercel`.

Do not assume these local skills are present for every collaborator. This file is the source of truth for general repo guidance.

## Git And Collaboration Rules

- The working tree may contain user or other-agent changes. Do not revert, overwrite, or reformat unrelated changes.
- Check current file contents before editing files that may have been touched by others.
- Do not commit unless explicitly asked.
- Do not push or deploy unless explicitly asked.
- Do not commit generated outputs such as `dist/`, `.astro/`, `node_modules/`, or local Vercel output.
- Use pnpm for dependency changes and keep `pnpm-lock.yaml` in sync with `package.json`.
- Treat `.env*` files and credentials as secrets. Do not print or commit them.

## Deployment Notes

- The site is configured for static output with the `@astrojs/vercel` adapter.
- Use `pnpm run build` to verify production output before deployment.
- Create preview deployments by default when asked to deploy. Production deployment should only happen when explicitly requested.

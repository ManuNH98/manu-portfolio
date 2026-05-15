# Manu Portfolio

Personal portfolio built with Astro, Tailwind CSS, TypeScript, pnpm, and Vercel deployment.

## Stack

- Astro
- Tailwind CSS
- TypeScript
- Vercel
- Node.js

## Commands

Run all commands from project root:

- `pnpm install` — install dependencies
- `pnpm run dev` — start local dev server (`localhost:4321`)
- `pnpm run build` — build production output in `dist/`
- `pnpm run preview` — preview production build locally
- `pnpm run quality:check` — run Astro project checks

## AI Skills Workflow

This project has curated skills installed in `.agents/skills/` and they should be used intentionally by task type.

### Skill routing by task

- **Astro pages, components, collections, routing, config** → `astro`
- **UI layout/styling and responsive behavior** → `tailwind-css-patterns`
- **Higher-fidelity visual design and polish** → `frontend-design`
- **Accessibility audit and remediation (WCAG 2.2)** → `accessibility`
- **SEO metadata, structured data, sitemap/canonical improvements** → `seo`
- **Type-heavy refactors and reusable type utilities** → `typescript-advanced-types`
- **Backend/API/service work in Node.js** → `nodejs-backend-patterns`
- **Node architecture and framework decision-making** → `nodejs-best-practices`
- **Preview/production deployments to Vercel** → `deploy-to-vercel`

### Recommended implementation pipeline

For new features and page work, follow this order:

1. **Design and structure**
   - Start with `frontend-design` for direction and component-level UX.
2. **Framework implementation**
   - Use `astro` for page/component architecture and framework conventions.
3. **Styling system**
   - Apply `tailwind-css-patterns` for responsive utility patterns.
4. **Type safety**
   - Apply `typescript-advanced-types` for robust shared types.
5. **Quality passes**
   - Run an **a11y pass** with `accessibility`.
   - Run an **SEO pass** with `seo`.
6. **Build and verify**
   - `pnpm run quality:check`
   - `pnpm run build`
   - `pnpm run preview`
7. **Deployment**
   - Use `deploy-to-vercel` (preview by default; production only when explicitly requested).

### Prompt patterns for consistency

Use these request patterns to trigger the right skill behavior:

- “Build a new Astro section/page for …”
- “Style this component with responsive Tailwind patterns.”
- “Do an accessibility pass on this page and fix WCAG issues.”
- “Optimize this route for SEO (meta, canonical, structured data).”
- “Refactor these TypeScript types for stronger compile-time safety.”
- “Create a preview deployment and share the Vercel URL.”

### Definition of done (feature-level)

Before considering feature work complete:

- Astro checks pass (`pnpm run quality:check`)
- Production build succeeds (`pnpm run build`)
- Accessibility issues addressed for new/changed UI
- SEO essentials present for new/changed pages
- Preview deployment created for review when requested

## Project Structure

```text
/
├── public/
├── src/
├── .agents/
│   └── skills/
└── package.json
```

`src/pages/` defines route-based pages. Shared components should live in `src/components/` and static assets in `public/`.

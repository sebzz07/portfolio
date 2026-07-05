# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Git workflow (required)

- `main` is protected on GitHub (PR required): never attempt to push directly to `main`.
- Always create a dedicated branch for any change (e.g. `claude/fix-xxx`).
- Once work is done, push the branch and open a pull request rather than merging it yourself.

## Commands

All commands run from `portfolio/` (this directory):

| Command           | Action                                        |
| :----------------- | :-------------------------------------------- |
| `npm install`       | Install dependencies                          |
| `npm run dev`       | Start local dev server (default `localhost:3000`) |
| `npm run build`     | Build production site to `./dist/`            |
| `npm run preview`   | Preview the production build locally          |
| `npm run astro ...` | Run Astro CLI commands, e.g. `astro check`    |

There is no test suite, linter, or formatter configured in this project. `npm run astro check` is the closest thing to a type-check (validates `.astro` files and content collection schemas against `tsconfig.json`, which extends `astro/tsconfigs/base`).

## Architecture

This is an Astro static site (Astro ^2.4, no UI framework — components are `.astro` files with scoped `<style>` blocks and vanilla `<script>`/Custom Elements where interactivity is needed, e.g. `ThemeToggle.astro`). Site copy is in French; this is Sébastien Dru's freelance developer portfolio.

- **Content collection (`src/content/work/*.md` + `src/content/config.ts`)**: each Markdown file is one portfolio project, validated against a shared Zod schema (`title`, `description`, `publishDate`, `tags`, `img`, `img_alt`). Adding a project is just adding a new `.md` file here — no route or component changes needed.
- **Dynamic routing (`src/pages/work/[...slug].astro`)**: uses `getStaticPaths()` to generate one static page per entry in the `work` collection at build time. `src/pages/work.astro` lists all projects (sorted by `publishDate` descending) via `PortfolioPreview.astro` cards; the two files are the list/detail pair for the same collection.
- **Layout composition**: every page wraps content in `BaseLayout.astro`, which pulls in `MainHead.astro` (meta tags, font preloading, and the theme-detection inline script), `Nav.astro`, and `Footer.astro`. Page-specific `<Hero>` + section components are composed inside pages (`index.astro`, `about.astro`, `work.astro`).
- **Theming**: dark/light mode is applied as a `theme-dark` class on `<html>`. A blocking inline script in `MainHead.astro` sets the initial class before paint (reads `localStorage`/`prefers-color-scheme`, avoiding flash-of-wrong-theme) and installs a `MutationObserver` that persists any later class change back to `localStorage`; `ThemeToggle.astro` is just a custom element that toggles the class on click — it doesn't handle persistence itself. CSS variables in `BaseLayout.astro` and `global.css` branch on `:root.theme-dark` for background images and colors.
- **Icons (`Icon.astro` + `IconPaths.ts`)**: icons are inline SVG paths keyed by name in `IconPaths.ts`; `Icon.astro`'s `icon` prop is typed as `keyof typeof iconPaths`, so adding a new icon means adding an entry to that map, not a new component.
- **Design tokens (`src/styles/global.css`)**: global CSS custom properties (colors, spacing, gradients, `--shadow-*`, `--text-*`) that components consume via `var(...)`; there's no Tailwind or CSS-in-JS layer.
- Static assets (images, background variants per theme/breakpoint, CV PDF) live in `public/assets/`.

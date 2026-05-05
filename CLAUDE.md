# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Flujo de trabajo obligatorio

Antes de realizar cualquier cambio en el código:

1. **Explicar** qué se va a cambiar y por qué, incluyendo el razonamiento detrás de la decisión.
2. **Ofrecer** profundizar en cualquier parte del cambio que el usuario quiera entender mejor.
3. **Esperar confirmación explícita** del usuario antes de aplicar cualquier modificación.

Nunca aplicar un cambio directamente. Toda edición debe ser validada por el usuario primero.

---

## Project Overview

A static fan site dedicated to author TJ Klune, built with plain HTML and CSS — no build tools, no JavaScript framework, no package manager. Open any `.html` file directly in a browser to preview it.

## Structure

```
index.html          # Home page
pages/
  libros.html       # Books catalog (grid of book covers linking to tjklunebooks.com)
  sobre.html        # About the author
  reseñas.html      # Reviews (includes a review submission form with star rating)
  contacto.html     # Contact form
css/
  style.css         # All page-level styles (sections, grid, footer, forms, etc.)
  header.css        # Header/navbar styles and responsive breakpoint (max-width: 900px)
img/                # All images (book covers, photos, icons, backgrounds)
```

## CSS Architecture

- `header.css` handles only the `<header>` element and its children. All other styles live in `style.css`.
- Both stylesheets are loaded on every page via `<link>` tags (relative paths adjust by depth: `./css/` from root, `../css/` from `pages/`).
- Google Fonts are loaded via `<link>`: **Playwrite Norge** for headings, **Oswald** for body text.
- Color palette: primary blue `#48A1D9`, secondary green `#678C42`, text `#333333`, backgrounds `#fafafa` / `whitesmoke` / `#f4f4f4`.

## Navigation Conventions

- Each page marks its own `<a class="nav-link">` with the additional `active` class.
- The `active` style applies a wavy underline (defined in `header.css`).
- `index.html` does **not** have a favicon `<link>` tag; all pages under `pages/` do (`../img/favicon.ico`).
- The home page header has social icons instead of the search form that appears on inner pages.

## Known Issues

- `index.html` references `./img/bookcover-heat.jpg` in the image grid, but that file does not exist in `img/`.
- There is a malformed HTML attribute on line 94 of `index.html`: `class="orphanage>` (missing closing quote).
- Several book cover images referenced in `libros.html` (e.g., `bookcover-somewhere.jpg`, `bookcover-who.jpg`, `bookcover-heat.jpg`, `bookcover-movie.jpg`, `bookcover-withered.jpg`) are missing from `img/`.
- The `.artwork div` in `style.css` has a duplicate `display` property (`display: ruby` overridden by `display: flex`).

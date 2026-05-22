# ARISE Summer Camp 2026

Welcome to the ARISE Summer Camp landing page project! 
This document serves as a strict guide for any human developer, AI agent, or tool contributing to this codebase.

## 🚀 Tech Stack & Philosophy
This project is built using **pure Vanilla HTML, CSS, and Javascript**. 
**Do not introduce frameworks** (like React, Vue, or TailwindCSS) or build steps. The goal is blazing fast 60FPS performance and a premium, highly interactive aesthetic without any dependencies.

- **Entry Point:** `index.html`
- **Hosting:** Vercel (Auto-deploys static HTML on GitHub pushes)
- **Forms Integration:** Tally.so Javascript API (Popups)

## 🎨 Design System & UI/UX Guidelines
The site employs a **Vibrant Light Theme** inspired by a sophisticated, high-end editorial aesthetic.

### Typography
Do not introduce new font families unless strictly requested.
- **Headings (Serif):** `Playfair Display` (Elegant, used for massive titles)
- **Body (Sans-serif):** `Plus Jakarta Sans` (Clean, highly legible)
- **Metadata (Mono):** `JetBrains Mono` (Used for dates, locations, and button kickers)

### Color Palette
- **Background:** `#fdfaf6` (Warm off-white, never pure white)
- **Primary Accent:** `#00924a` (Harvest Green — extracted directly from the logo)
- **Text:** `#0a2e1c` (Deep forest green for legibility instead of pure black)

### Icons (No Emojis)
- Emojis are strictly forbidden to maintain a premium feel.
- We use **Phosphor Icons** via a CDN script in the `<head>`. 
- Implementation looks like: `<i class="ph ph-backpack"></i>`

## 🏗️ Core Architectural Features
If you are modifying the layout, you must preserve these key interactive elements:

### 1. The Negative Footer Reveal
The footer does **not** sit at the bottom of the document flow. 
- The `<footer id="negativeFooter">` is `position: fixed` at the bottom with a low `z-index`.
- The main content is wrapped in `<div id="siteWrapper">` which acts as a sliding curtain over the footer.
- **Javascript Logic:** On load/resize, Javascript dynamically sets the `margin-bottom` of the wrapper to match the exact height of the footer so the scroll ends precisely when the footer is fully revealed. This is disabled on mobile devices for better touch scroll performance.

### 2. Magnetic Glass Buttons
The registration buttons (`.role-btn`) feature a sophisticated magnetic hover effect.
- **Javascript Logic:** Mouse movement over `.magnetic-wrap` triggers a translate effect pulling the button toward the cursor.
- **CSS Glow:** Mouse coordinates are passed to CSS variables (`--mx`, `--my`) to create a dynamic radial gradient glow *inside* the frosted glass button.

### 3. 3D Tilt Flyer
The main hero image (`.flyer-img`) is wrapped in a container that reacts to mouse movement.
- **Javascript Logic:** Calculates cursor position and applies dynamic `rotateX` and `rotateY` transforms to create a deep 3D perspective effect. It also moves a subtle `mix-blend-mode` glare over the image for realism.

## 📝 Tally Form Integrations
The site triggers Tally.so forms using their Javascript API (`Tally.openPopup`). 
- Do not use hidden iframes.
- The `roleData` object in the `<script>` block controls which form ID is mapped to which button.
- We explicitly disable Tally's native emojis in the configuration options to keep the UI strictly aligned with Phosphor icons.

## 💻 Contribution Workflow
1. Pull the latest code (`git pull`).
2. Make your edits strictly to `index.html` (or add assets).
3. Test by opening `index.html` locally in a browser or spinning up a simple local server (`python -m http.server`).
4. Commit and push your changes to the `main` branch. Vercel will automatically deploy the updates.

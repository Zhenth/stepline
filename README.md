# StepLine

Premium shoe catalog built with **Vue 3** + **Vite** + **Tailwind CSS**.

## Tech Stack

- **Vue 3** (Composition API with `<script setup>`)
- **Vite 8** (dev server & production bundler)
- **Tailwind CSS 3** (utility-first styling with dark mode)
- **Lucide Vue Next** (icons)
- **Google Fonts** (Inter, Montserrat)

## Getting Started

```bash
# Install dependencies
npm install

# Start development server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview
```

## Project Structure

```
src/
├── assets/
│   └── main.css         # Tailwind directives + custom styles
├── components/
│   ├── AppHeader.vue    # Navigation, search, theme toggle
│   ├── HeroSection.vue  # Auto-sliding hero banner
│   ├── AboutSection.vue # About us section
│   ├── CatalogSection.vue # Brand filters + product slider
│   ├── ProductCard.vue  # Individual product card
│   ├── ProductModal.vue # Product detail modal
│   └── AppFooter.vue   # Footer with contact info
├── data/
│   └── products.js      # Product catalog data
├── App.vue              # Root component
└── main.js              # App entry point
```

## Features

- 🎨 Dark/Light mode with persistence
- 🔍 Real-time product search
- 🏷️ Brand filtering (Nike, Adidas, Puma, NB, Asics)
- 🖼️ Product detail modal with image gallery
- 🎠 Auto-sliding hero banner
- 📱 Fully responsive design

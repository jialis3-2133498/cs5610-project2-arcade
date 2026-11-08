# Jiali Sheng's Arcade

A web arcade built with Svelte 5 and SvelteKit 3 for CS5610 Web Development — Project 2: 2048 and a Published Package.

This project includes a 2048 game and a mini crossword puzzle migrated from Project 1. It uses a separately published npm package for the core 2048 game logic.

## Live Website

[Play Jiali Sheng's Arcade](https://jialis3-2133498.github.io/cs5610-project2-arcade/)

## Features

### 2048

- A 4 × 4 game board with directional tile movement and merging.
- Keyboard arrow controls and on-screen directional buttons for touch devices.
- Score tracking and a best score saved in browser local storage.
- Random tile spawning after valid moves.
- A New Game button to restart the game.
- Win detection at 2048, with an option to continue playing.
- Game-over detection when no valid moves remain.

### Mini Crossword Puzzle

- A crossword puzzle migrated from Project 1 into Svelte.
- Interactive letter-entry cells with Across and Down clues.
- A Clear button to reset the puzzle.
- Responsive layout for mobile and desktop screens.

### Website

- Home, Crossword, About, Contact, and 2048 pages.
- Shared navigation and layout components.
- Responsive design for different screen sizes.
- Accessibility features, including keyboard interaction, accessible labels, and live status announcements.

## Technologies

- Svelte 5
- SvelteKit 3
- JavaScript
- HTML and CSS
- Vite
- Node.js and npm
- GitHub Pages and GitHub Actions

## npm Package

The core 2048 game logic is provided by my separately published package:

[@jialisheng/arcade-core](https://www.npmjs.com/package/@jialisheng/arcade-core)

The package provides pure functions for directional movement, tile spawning, and move availability checks. Separating this logic from the Svelte interface makes it easier to test and reuse.

## Installation and Local Development

Clone the repository:

```bash
git clone https://github.com/jialis3-2133498/cs5610-project2-arcade.git
cd cs5610-project2-arcade
```

Install dependencies:

```bash
npm install
```

Start the development server:

```bash
npm run dev
```

Open the local URL displayed in the terminal.

## Testing and Building

Check the Svelte project for errors and warnings:

```bash
npm run check
```

Build the application:

```bash
npm run build
```

The project uses `@sveltejs/adapter-static` to generate a static website for GitHub Pages.

The core game logic is tested separately in the `arcade-core` package using Node.js tests.

## Deployment

The website is deployed to GitHub Pages using GitHub Actions.

The deployment workflow is located at:

`.github/workflows/deploy.yml`

Pushing changes to the `main` branch triggers the workflow, which installs dependencies, checks the Svelte project, builds the static website, and deploys the generated files.

## Project Structure

```text
src/
├── lib/
│   ├── components/      # Reusable Svelte components
│   └── state/           # Shared reactive state
├── routes/
│   ├── 2048/           # 2048 game
│   ├── about/          # About page
│   ├── contact/        # Contact page
│   ├── crossword/      # Crossword game
│   ├── +layout.svelte  # Shared layout
│   ├── +layout.js      # Prerendering configuration
│   └── +page.svelte    # Home page
└── app.css             # Global styles
```

## Accessibility and Responsive Design

The website supports keyboard navigation and responsive layouts across mobile, tablet, and desktop screen sizes.

The 2048 game includes on-screen direction controls, accessible button labels, and live announcements for score changes and game status.

All five deployed routes achieved Lighthouse Accessibility scores above 80.

## Author

Jiali Sheng

CS5610 — Web Development, Fall 2026

Northeastern University
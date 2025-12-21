# Sz Games - Project Context

## Overview
**Sz Games** is a static web-based game aggregation platform designed primarily for school environments. It focuses on providing "unblocked" access to web games using techniques like tab cloaking and `about:blank` embedding. The site features a library of over 250 games, including retro titles, emulators, and popular web games.

## Architecture
The project is a **Static Website** hosted on GitHub Pages. It does not use a backend database or server-side rendering language (like PHP or Python). instead, it relies on:
*   **Frontend:** HTML5, CSS3, and Vanilla JavaScript.
*   **Data Storage:** A large JavaScript array (`gamesData`) within `games.js` acts as the client-side database.
*   **Rendering:** The `script.js` file reads the `gamesData` array and dynamically generates the HTML for the game grid in the browser.

## Key Files & Directories

### Core
*   **`index.html`**: The main entry point. Contains the site structure, navigation bars, ads configuration, and the empty container (`#games`) where games are injected.
*   **`games.js`**: The most critical data file. Contains the `gamesData` constant, an array of objects where each object represents a game (ID, name, category, URL, image source).
*   **`script.js`**: The main application logic. It handles:
    *   **Rendering:** Iterates through `gamesData` to create and append game cards to the DOM.
    *   **Search & Filter:** Implements the search bar logic and category filtering (e.g., "Shooter", "Casual").
    *   **UI Interactions:** Manages menus, scroll-to-top buttons, and "maintenance mode" screens.
*   **`style.css` / `styles.css`**: Global styling for the application.

### Content
*   **`games/`**: Directory containing HTML files for individual games or iframed content.
*   **`cover/`**: Stores game thumbnails and cover images.
*   **`_config.yml`**: Minimal Jekyll configuration (primarily for GitHub Pages settings).

## Development Workflow

### 1. Running Locally
Since this is a static site, you can serve it using any simple HTTP server.
*   **Python:** `python3 -m http.server 8000`
*   **Node.js:** `npx http-server .`
*   **VS Code:** Use the "Live Server" extension.

### 2. Adding a New Game
To add a game to the site, you strictly modify **`games.js`**:
1.  Open `games.js`.
2.  Add a new object to the `gamesData` array in the following format:
    ```javascript
    {
      id: 'Game Unique Name',
      name: 'Display Name',
      categories: ['Category1', 'Category2'], // e.g., 'Shooter', 'Casual'
      url: 'https://path-to-game.com', // Can be local path or external URL
      imgSrc: './path/to/image.png' // Usually in the cover/ directory
    },
    ```
3.  Ensure the image exists in the specified path (usually `cover/`).

### 3. Modifying Logic
*   **UI Changes:** Edit `index.html` for structure or `script.js` for dynamic behavior.
*   **Styling:** Edit `styles.css`.
*   **Note:** The project uses direct DOM manipulation (`document.getElementById`, `createElement`). There is no build step (Webpack/Vite) or framework (React/Vue).

## Project Features
*   **Tab Cloaking:** Disguises the tab to look like Google or other educational sites.
*   **About:Blank Embedding:** Opens games in an `about:blank` page to bypass some extension-based blockers.
*   **Panic Button:** A feature to quickly hide the game.
*   **PWA Support:** `service-worker.js` and `manifest.json` indicate Progressive Web App capabilities.

## Conventions
*   **Variable Naming:** CamelCase is generally used (e.g., `gamesData`, `renderGames`).
*   **Formatting:** Standard JS formatting.
*   **Dependencies:** No `package.json` means no NPM dependencies. All libraries (like FontAwesome, Google Ads) are loaded via CDN in `index.html`.

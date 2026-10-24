# 🌍 World Explorer — Country Discovery Web Application

A modern, responsive country discovery web application built with **Vanilla JavaScript** and **Tailwind CSS**, powered by the **REST Countries API**. Discover countries across the globe, view detailed geographical and political data, navigate interactive border countries, bookmark favorites with persistent local storage, and compare nations side-by-side.

---

## 🚀 Live Demo & Repository
- **Live URL:** [World-Explorer]([#-deployment-guide](https://world-explorer-ebon-two.vercel.app/))
- **GitHub Repository:** [https://github.com/hemantsharma7707/World-Explorer](https://github.com/hemantsharma7707)

---

## 📋 Features Checklist (Rubric Aligned)

### 1. Browse & Discovery View
- [x] **250+ Country Cards**: Dynamic rendering of all countries with high-res flag, country name, population, capital, and region.
- [x] **Performance Optimization**: Uses `document.createDocumentFragment()` to render the full 250-country dataset smoothly without UI freezing.
- [x] **Formatted Metrics**: Population and area formatted with commas (e.g., `1,408,044,253`) via `Number.toLocaleString()`.

### 2. Search, Filter & Sort
- [x] **Debounced Search**: 350ms debouncing ensures instant client-side filtering without excessive recalculation on every keystroke.
- [x] **Region Filter**: Filter by region (*Africa, Americas, Asia, Europe, Oceania*).
- [x] **Multi-criteria Sorting**:
  - Name: A → Z & Z → A
  - Population: High → Low & Low → High
  - Area: Largest first & Smallest first
- [x] **Result Counter**: Real-time feedback showing the count of matched countries.

### 3. Detail View & Interactive Navigation
- [x] **Comprehensive Country Details**: Displays native name, population, region, subregion, capital, area, top-level domain (TLD), currencies, and official languages.
- [x] **Direct Google Maps Link**: One-click navigation to explore the country coordinates on Google Maps.
- [x] **Interactive Border Country Chips**: Bordering countries are dynamically resolved to their common names and displayed as interactive chips — clicking any border chip smoothly jumps straight to that country's detail page.

### 4. Favorites & Comparison Mode
- [x] **LocalStorage Persistence**: Add or remove favorites using heart icons (`❤️` / `🤍`). Bookmarked countries persist across browser refreshes and browser restarts.
- [x] **Navbar Badge**: Dynamic badge in the navigation bar displaying the current count of saved favorites.
- [x] **Side-by-Side Comparison**: Select any two favorite nations to view their population, area, region, subregion, capital, currencies, and languages side-by-side with an interactive VS divider.

### 5. UI Polish & Visual States
- [x] **Three Distinct UI States**:
  - **Loading State**: 12 responsive skeleton shimmer cards during API requests.
  - **Error State**: Friendly error screen with a user-triggered "Try Again" retry button.
  - **Empty State**: Clear prompt when no countries match search or filter queries.
- [x] **Dark Mode Toggle**: Persistent dark mode (saved to `localStorage`) with instant theme switching.
- [x] **Responsive Design**: Mobile-first layout with smooth transitions, hover lift effects, and accessible controls.

---

## 🛠️ Technical Stack & Architecture

- **Markup:** Semantic HTML5 (`header`, `main`, `section`, `footer`)
- **Styling:** [Tailwind CSS v3](https://tailwindcss.com/) (loaded via CDN, strictly no external CSS files as required)
- **Logic:** Vanilla JavaScript (ES6+) — Single file architecture inside `<script>`
- **API Source:** REST Countries API (`v3.1`) with high-availability mirror fallback
- **Storage:** Browser `localStorage` API

---

## 🧠 Technical Requirements Met

| Requirement | Implementation Details in `index.html` |
| :--- | :--- |
| **Vanilla JS Only** | No React, Vue, jQuery, or third-party JS libraries used. |
| **Dynamic DOM Creation** | All cards and elements constructed using `document.createElement`, `appendChild`, and `classList`. No hardcoded HTML results. |
| **Array Methods** | Meaningful usage of `Array.prototype.filter()`, `sort()`, `map()`, `find()`, and `forEach()`. |
| **Event Delegation** | Single click listener on `#countriesGrid` and `#favoritesGrid` handling card navigation and favorite toggles via `e.target.closest()`. |
| **Async / Await** | Modern asynchronous programming with `async/await` throughout; zero `.then()` promise chains. |
| **Try / Catch Handling** | Robust error boundaries wrapping all network fetches and fallbacks. |
| **Three Visible UI States** | Explicit `#loadingDiv`, `#errorDiv`, and `#emptyDiv` elements with toggle logic. |
| **User-Triggered Fetch** | Interactive retry button and real-time detail/compare queries beyond initial load. |
| **Persistence** | Synchronized JSON serialization (`JSON.stringify` / `JSON.parse`) via `localStorage`. |
| **Git Milestones** | Structured Git progression with 10+ meaningful commits, feature branch, and merged PR. |

---

## 💡 Code Walkthrough (For Presentation & Viva)

The code in `index.html` is organized into 14 clearly commented sections designed to be easy to read and explain:

1. **`1. Global Variables`**: Holds `allCountries` array in memory so filtering and sorting never re-fetch from the network.
2. **`2. API Functions`**: Contains `apiRequest()`, `fetchAllCountries()`, `fetchCountryByCode()`, and `fetchBorderCountries()` using `async/await` with `try/catch`.
3. **`3. Utility Functions`**: `formatNum()` formats numbers with commas (`1,000,000`), and `debounce()` waits 350ms after the user stops typing before triggering search.
4. **`4. LocalStorage — Favorites`**: Handles reading and writing an array of country CCA3 codes in `localStorage` under key `worldExplorer_favorites`.
5. **`5. Show / Hide Views`**: Simple view-switching function (`showView`) that toggles the `hidden` class on the 4 main application sections.
6. **`6. UI State Management`**: `showLoading()` renders 12 skeleton cards, `showError()` displays the error screen with retry, and `showEmpty()` shows "No countries found".
7. **`7. Create Country Card`**: Uses pure DOM methods (`document.createElement`) to build each card element dynamically with flag, name, stats, and favorite heart button.
8. **`8. Render Cards into Grid`**: Uses a `DocumentFragment` to batch DOM operations for high performance.
9. **`9. Filter & Sort`**: Uses `Array.filter()` to match search keyword and region, then `Array.sort()` with `localeCompare` and numeric comparisons.
10. **`10. Detail View`**: Fetches full country metadata and border countries, rendering detailed lists and clickable border chips.
11. **`11. Favorites View`**: Uses `Array.find()` to locate favorite objects from `allCountries` and renders them in a grid.
12. **`12. Compare View`**: Provides two dropdowns to pick countries from favorites and displays their stats side-by-side with a "VS" badge.
13. **`13. Dark Mode`**: Checks and toggles the `'dark'` class on `document.documentElement` and stores preference in `localStorage`.
14. **`14. Initialize App`**: Called on `DOMContentLoaded`. Sets up **Event Delegation** on the grid parent, debounced inputs, and performs initial load.

---

## 💻 How to Run Locally

1. **Clone the repository:**
   ```bash
   git clone https://github.com/hemantsharma7707/World-Explorer.git
   cd World-Explorer
   ```

2. **Open in browser:**
   Simply double-click `index.html` or open it with your favorite local server:
   ```bash
   # Using VS Code Live Server or Python:
   python3 -m http.server 3000
   ```
   Open `http://localhost:3000` in your web browser.

---

## 🚀 Deployment Guide (Vercel)

This application is completely static (single file `index.html`), making deployment to **Vercel** instant:

1. Push this repository to GitHub.
2. Go to [vercel.com](https://vercel.com/) and click **Add New Project**.
3. Import your `World-Explorer` repository.
4. Keep all build settings as default (Framework Preset: **Other**, Build Command: empty, Output Directory: `./`).
5. Click **Deploy**. Your site will be live within seconds!

---

## 📸 Screenshots

*(Add screenshots of Browse View, Detail View with border chips, and Compare View after deployment)*

| Browse View | Country Detail View | Compare View |
| :---: | :---: | :---: |
| ![Browse View](https://via.placeholder.com/400x250?text=Browse+View) | ![Detail View](https://via.placeholder.com/400x250?text=Detail+View) | ![Compare View](https://via.placeholder.com/400x250?text=Compare+View) |

---

## 👤 Author
- **Hemant Sharma**
- GitHub: [@hemantsharma7707](https://github.com/hemantsharma7707)
- Email: `hemantjvd@gmail.com`

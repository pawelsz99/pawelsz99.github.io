# AGENTS.md - Developer Guidelines

## Project Overview

This is a static portfolio website (devportfolio-template) built with:
- **Gulp** - Task automation for JS/SCSS compilation
- **jQuery** - JavaScript interactivity
- **SCSS** - CSS preprocessing
- **Babel** - JavaScript transpilation

## Build Commands

### Install Dependencies
```bash
npm install
```

### Development
```bash
npm run watch
```
Watches `./js/scripts.js` and `./scss/styles.scss` files and compiles on changes.

### Manual Build (if needed)
```bash
npx gulp scripts   # Compile and minify JS
npx gulp styles    # Compile and minify SCSS
```

### Running a Single Test
No test framework is currently configured. To add tests, consider:
- Jest for unit testing
- Cypress or Playwright for E2E testing

## Code Style Guidelines

### JavaScript (js/scripts.js)

- **Pattern**: Use IIFE `(function($) { ... })(jQuery);` to avoid global pollution
- **Semicolons**: Always use semicolons at statement end
- **Quotes**: Use single quotes for strings
- **Indentation**: 4 spaces
- **Variable declarations**: Use `var` for jQuery-wrapped variables (legacy style), `let`/`const` for new code
- **jQuery**: Prefix jQuery objects with `$` (e.g., `$this`, `$userContent`)
- **Comments**: Use block comments `/* */` for file headers, inline `//` for explanations
- **Functions**: Use named function expressions for clarity

### SCSS (scss/styles.scss)

- **Indentation**: 4 spaces
- **Nesting**: Limit nesting to 3-4 levels deep
- **Variables**: Use variables for colors, fonts, and spacing
- **Prefixes**: Autoprefixer handles vendor prefixes automatically
- **Output**: Compiled to compressed CSS in `./css/`

### Gulp (gulpfile.js)

- **Imports**: Use `require()` (common in Gulp 4)
- **Tasks**: Use `gulp.task()` and `gulp.series()` for task composition
- **Error handling**: Always include plumber error handlers

### HTML

- **Structure**: Semantic HTML5 elements
- **Classes**: Use lowercase with hyphens (e.g., `vtimeline-point`)
- **IDs**: Use lowercase with hyphens

### Naming Conventions

| Type | Convention | Example |
|------|------------|---------|
| Files | lowercase with hyphens | `scripts.js`, `styles.scss` |
| Functions | camelCase | `initPortfolio()` |
| Variables | camelCase | `scrollDistance` |
| CSS Classes | lowercase with hyphens | `vtimeline-content` |
| Constants | UPPER_SNAKE_CASE | `MAX_ITEMS` |

### Error Handling

- **JavaScript**: Wrap async operations in try/catch, log errors to console
- **Gulp**: Use plumber for non-crashing errors in watch mode
- **SCSS**: Use `sass.logError` for compile errors

### Best Practices

1. **Never commit secrets** - Keep API keys, tokens out of the codebase
2. **Minify in build** - Production JS/CSS is minified automatically
3. **Comment complex logic** - Explain non-obvious code sections
4. **Keep it simple** - This is a static site; avoid over-engineering

## File Structure

```
.
├── index.html          # Main portfolio page
├── ai-swimwear.html    # Additional page
├── css/                # Compiled styles (generated)
├── js/
│   ├── scripts.js      # Source JavaScript
│   └── scripts.min.js  # Compiled JavaScript (generated)
├── scss/
│   └── styles.scss     # Source styles
├── gulpfile.js         # Build configuration
├── package.json        # Dependencies
└── images/             # Image assets
```

## Dependencies

- **devDependencies**: `@babel/core`, `@babel/preset-env`, `gulp`, `gulp-autoprefixer`, `gulp-babel`, `gulp-plumber`, `gulp-rename`, `gulp-sass`, `gulp-uglify`

## Notes for AI Agents

- This is a simple static site; avoid adding complex frameworks
- Any new JavaScript should be added to `js/scripts.js`
- Any new styles should be added to `scss/styles.scss`
- Run `npm run watch` during development to auto-compile changes
- The site uses jQuery - prefer jQuery methods over vanilla JS for consistency
- No TypeScript, Prettier, or ESLint currently configured

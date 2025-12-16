# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

"草药仙踪" (Herbal Fairy Trail) is a static HTML/CSS website about traditional Chinese herbal medicine. The site features interactive educational content including stories, herb exploration, personality tests, and an AI assistant for herbal medicine questions.

## Project Structure

The codebase is organized as a multi-page static website:

- **Root HTML files**: Main navigation pages (`index.html`, `home.html`, `search.html`, `mys.html`, `interact.html`, `soul.html`, `start.html`)
- **`html-mys/`**: Story/narrative content pages
- **`html-interact/`**: Interactive features (challenge games, health assistant, video list)
- **`html-soul/`**: Personality test pages
- **`css/`**: Stylesheets organized by page (`base.css`, `common.css`, and page-specific CSS)
- **`pic/`**: Image assets organized by section (home, search, mys, soul, interact)
- **Custom font**: `站酷小薇logo体.OTF` used throughout the site

## Navigation Structure

The site has 5 main sections accessible from the header navigation:

1. **首页 (Home)** - `home.html`: Landing page with section overview
2. **神秘故事 (Mysterious Stories)** - `mys.html`: Story chapters that link to `html-mys/stories.html` with chapter parameters
3. **草药探寻 (Herb Exploration)** - `search.html`: Regional herb catalog organized by 6 Chinese regions
4. **趣味互动 (Interactive Fun)** - `interact.html`: Links to 3 sub-features:
   - Challenge game (`html-interact/challenge.html`)
   - Health assistant (`html-interact/assistant.html`)
   - Video list (`html-interact/video-list.html`)
5. **草药仙灵 (Herb Spirits)** - `soul.html`: Herb encyclopedia with AI assistant and personality test

## Key Technical Patterns

### CSS Architecture
- `base.css`: Global resets, custom font (`@font-face`), body background
- `common.css`: Shared header/navigation styles
- Page-specific CSS files match their HTML counterparts

### JavaScript Patterns in `soul.html`
- **Mode switching**: Three modes (问道/theory, 闲聊/chat, 求方/recipe) for the AI assistant
- **Keyword matching**: Simple keyword-based Q&A system stored in `qaData` object
- **Modal popups**: Two overlay systems - one for herb details, one for assistant responses
- **Sprite images**: Background positioning used for herb images (`background-position: 0px -190px`)

### URL Parameters
- `html-mys/stories.html?chapter=N` - Chapter navigation (0-4)
- Query parameters used for content switching

### Relative Path Conventions
- Root pages reference assets as `./pic/`, `./css/`
- Subdirectory pages use `../pic/`, `../css/`

## Common Development Tasks

### Opening the site
Open `index.html` in a browser (no build process required - pure static HTML/CSS/JS)

### Adding new herbs to the encyclopedia
1. Add herb data to `herbData` array in `soul.html` (name, sprite offset, content)
2. Add corresponding card HTML in `.cards` section
3. Update sprite image if needed (`./pic/soul/pics-herb.png`)

### Adding Q&A content to the assistant
Edit the `qaData` object in `soul.html` under the appropriate mode (recipe/theory/chat). Each entry needs `keywords`, `title`, and `content`.

### Modifying navigation
Update the header `.nav` section in each HTML file (structure is duplicated across pages)

## Important Notes

- No build system, package manager, or dependencies
- All JavaScript is inline `<script>` tags (no external JS files)
- Chinese language content throughout
- Custom font must be present for proper rendering
- Images are essential to the design (not decorative)

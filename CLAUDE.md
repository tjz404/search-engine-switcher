# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Custom fork of [F9y4ng/GreasyFork-Scripts](https://github.com/F9y4ng/GreasyFork-Scripts), containing only the **Search Engine Assistant** userscript (`Google & Baidu Switcher.user.js`). This is a Tampermonkey/Greasemonkey/Violentmonkey userscript — no build system, no bundler, no tests, no linting. The script runs directly in the browser via a script manager extension.

The `@updateURL` is set to `none` to prevent the upstream original from overwriting customizations.

## Fork Customizations

All custom changes live in `Google & Baidu Switcher.user.js`:

- **Two new search engines**: Bilibili (siteTypeID 19, ~line 1784) and Xiaohongshu (siteTypeID 20, ~line 1803), added to the `listSite` object following the same property structure as existing engines
- **Bing quick-jump buttons**: Google/Bilibili/Xiaohongshu jump buttons injected into Bing's search box area (~line 2533), rendered inside a closed Shadow DOM
- **Visual styling**: Gradient backgrounds using each engine's brand colors, hover animations with `translateY(-1px)` + box-shadow, consistent `2px solid #f6f7f8` borders

## Architecture

The entire script (~3100 lines) is a single IIFE that bootstraps with three window references: `window`, `unsafeWindow`, and a safe sandbox window (created via `GM_addElement("iframe")`). Key internal structure:

- **`toolkit` / `secureVars`** (~line 292): Sandboxed browser APIs to avoid page-level prototype pollution
- **`listSite` object** (~line 1660+): All supported search engine definitions — each entry specifies `siteTypeID`, URLs, CSS for buttons (`buttonCssText`), DOM selectors (`mainSelector`, `resultListProp`), keyword highlight selectors, and optional `antiRedirectFn`/`antiAdsFn` callbacks
- **`newSiteType` enum** (~line 1825+): Maps hostname regex patterns to site type constants
- **Shadow DOM button injection**: Each engine's switcher buttons are rendered inside a closed Shadow DOM attached to a container element, styled via `adoptedStyleSheets` or inline `<style>` fallback

### Adding a New Search Engine

1. Add `@match` pattern in the UserScript header
2. Add entry to `listSite` object with: `siteTypeID` (next sequential int), `siteButtonName`, `siteHostName`, `webURL`, `mainSelector` (where to anchor buttons), `buttonCssText`, `resultListProp`, and optionally `antiAdsFn`
3. Add corresponding entry in `newSiteType` with hostname regex
4. If adding Bing quick-jump buttons, extend the HTML/CSS/click-handler block (~line 2533)

## Files

- `Google & Baidu Switcher.user.js` — the userscript (sole deliverable)
- `lib/gbCookies.js` — cookie utility used by the search engine assistant (loaded from upstream CDN via `@require`, local copy is reference)
- `lib/frColorPicker.js` — color picker for the Font Rendering script (not used by this fork, retained from upstream)

## Language

README and UI strings are bilingual (Chinese/English). The script detects locale via `checkLocalChineseLanguage()` and uses `IS_CHN` to toggle between Chinese and English button labels.

## AI Assistant Operational Rules (CRITICAL)
- **Prevent Truncation**: When using file editing tools (Write/Edit) on large files like `Google & Baidu Switcher.user.js` (~3100 lines), **NEVER** output more than 50 lines of code at once.
- **Chunking**: You MUST split large modifications into multiple smaller chunks (≤ 50 lines per tool call) to prevent `[FATAL] TRUNCATED` stream errors.
- **Targeted Edits Only**: Always use targeted replacements (Search/Replace or targeting specific line numbers) rather than attempting to rewrite or overwrite the entire file.
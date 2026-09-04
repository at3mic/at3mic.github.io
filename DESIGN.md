# at3mic.github.io design contract

## 0. Research Log
- Existing `hugo-theme-terminal/v4` remains the structural foundation: header, menu, posts, taxonomy, footer, and built-in JavaScript stay intact.
- Existing local templates, `static/style.css`, content, and rendered routes were inspected before this redesign.
- Direction selected from user feedback: analog studio with a restrained terminal accent—warm paper, ink typography, terracotta signal color, and monospace utility text.

## 1. Direction
An analog developer studio: editorial rather than dashboard-like, tactile rather than glossy. The Terminal theme supplies the dependable Hugo architecture; custom overrides give it a warmer paper canvas, serif display type, ruled surfaces, and deliberate orange/red accents.

## 2. Tokens
- `--background`: `#f4efe6` paper
- `--surface`: `#e8dfd2` card/panel
- `--foreground`: `#211d1a` ink
- `--muted`: `#6d6258` secondary ink
- `--accent`: `#b4472d` terracotta signal
- `--accent-strong`: `#7d2f22` deep terracotta
- `--gold`: `#bd8438` ochre detail
- `--line`: `#cfc2b2` ruled border
- `--radius`: `2px`
- Body size: `1rem`; body line-height: `1.7`
- Content measure: `70ch`; page gutter: `clamp(1rem, 5vw, 4rem)`

## 3. Typography and rhythm
Georgia provides an editorial display voice for headings; Fira Code remains available for code, metadata, labels, and navigation. Body copy uses a readable system sans stack. Uppercase labels use generous tracking. Vertical rhythm is based on a small set of spacing values rather than theme defaults.

## 4. Components
- Header: existing Terminal header/menu behavior, restyled as a masthead with ink logo, terracotta marker, and ruled navigation.
- Banner: existing image becomes a framed studio artifact with a warm border and responsive containment.
- Project feature: existing admonition remains live DOM and becomes a paper card with a terracotta edge.
- Posts/taxonomy: existing theme templates remain; cards, metadata, headings, and pagination inherit the same tokens.
- Code/tables: existing native scrolling behavior remains local to the content block.

## 5. Responsive behavior
The existing Terminal mobile menu stays in charge at the theme breakpoint. Gutters, masthead, banner, cards, lists, code, and tables shrink or scroll locally below 684px. No fixed-width element may exceed the viewport.

## 6. Accessibility
Preserve semantic theme markup, meaningful image alternatives, visible `:focus-visible` outlines, underlined links, readable contrast, native keyboard menu behavior, and reduced-motion support. Decorative color never carries meaning alone.

## 7. Performance and maintenance
No new runtime dependency, JavaScript layer, or deployment mechanism. Existing Hugo modules and self-hosted GitHub Actions workflow remain unchanged. The redesign is a focused override layer over the installed Terminal theme.

## 8. Accepted debt
The single banner remains a static asset. Font loading remains system-first; Fira Code is used for code and utility text without adding a font package.

## 9. Verification scenarios
1. Desktop homepage at 1280px: analog masthead, editorial headings, framed banner, project card, navigation, and footer render without overflow.
2. Mobile homepage at 375px: Terminal mobile menu remains usable, paper surfaces fit the viewport, text wraps, and code/table overflow stays local.
3. Adjacent routes `/posts/hello-world/`, `/posts/`, `/tags/`, `/categories/`, and a missing route retain the redesigned shared chrome and usable typography.
4. Build: `hugo build --gc --minify --cleanDestinationDir` exits 0 with expected routes/assets.

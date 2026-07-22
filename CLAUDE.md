# shreshthsaini.github.io

Personal academic site. Plain static HTML, no build system; every page inlines its own CSS. Blog posts live in `blogs/`, each as one standalone HTML file.

## Hard rules

- NEVER use em-dashes anywhere (prose, captions, commit messages). Restructure with commas, colons, periods, or parentheses. Keep colons in prose rare.
- NEVER add Claude/AI attribution: no Co-Authored-By trailers, no "Generated with" lines.
- Show changes for review before committing or pushing. Push only when Shreshth says push.

## Adding or editing a blog post

- Copy the skeleton from `blogs/rectified-flow.html`: nav, hover `toc-rail` with scroll-spy script, hero (title, serif subtitle, date + `.pill` tags), `article` in Crimson Pro, blue-left-border `.summary` thesis block, footer "Back to Scratch Pad". Drop MathJax/code CSS for non-technical posts.
- Add a card to the Writing section of `blogs.html` (newest first) and bump the `section-count`. Unpublished posts keep their card commented out with an `UNPUBLISHED` marker and are excluded from the count.
- Section headings use chip numbering: `<h2 id="sec-x"><span class="sec-num">01</span>Title</h2>`. Never "1)" style. References and Citation sections stay unnumbered.
- Figure captions: `<figcaption data-fig="Fig. N">` with manual sequential numbers per post. Style is italic muted Inter with a small gray uppercase prefix, no box. Boxed styles (`.aside-note`, `.callout-highlight`, `.deep-dive`) are for notes only, never captions. Mini-labels inside `.compare-grid` get no number.
- References list uses `.references` at 13px. Technical posts end with a Citation section: bare labeled BibTeX blocks in `<pre>`, no "please cite" lead-in text. Paper-backed posts include both the paper and the post BibTeX.
- Tables use the `cmp-table` / `result-table` pattern (Inter, subtle header band, wrapped in `.table-scroll` if wide).

## Interactive figures

- Every blog post opens with at least one hero figure placed right after the hero header (before the `.summary` block): an ABSTRACT, INTERACTIVE piece that captures the post's core idea without being a literal method diagram. Style inspiration is the header figures on Thinking Machines' blog (thinkingmachines.ai): generative, ambient, playable (a slider or cursor interaction), with a caption that ties the abstraction back to the post. Existing examples: the reflow transport bundle in `blogs/rectified-flow.html`, the guidance particle field in `blogs/rectified-cfgpp.html`, the two-threads figure in `blogs/on-reneging-a-job-offer.html`.
- Every post always gets its Citation section (and captions/figures always carry proper citations where they draw on external work).
- Vanilla `<canvas>` only, no external libraries (CSP-free static site). Controls go in a `.fig-controls` row (range sliders, `.seg` tab buttons); widgets in a `.widget` card.
- Every canvas needs: explicit width:100% CSS (bare canvases default to 300px), devicePixelRatio-aware resize, `prefers-reduced-motion` fallback to a static frame with working controls.
- Prefer real math over canned animation: closed-form fields, exact simulations. Verify convergence numerically with node before shipping.
- Long-form posts with many topics can use the collapsible `details.topic-fold` + `part-band` pattern from `blogs/genai-interview-notes.html` (folds auto-open on hash links and before print).

## Site chrome

- MathJax via tex-svg CDN, `\( \)` inline and `\[ \]` display.
- Palette: accent #2563eb, slate text, amber #f59e0b for note borders; tag colors defined in `blogs.html`.
- `CLAUDE.md` and internal files are excluded from the published site via `_config.yml`.

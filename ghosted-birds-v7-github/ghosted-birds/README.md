# Ghosted Birds: opening graphic, two resizing rows and the Crissal Thrasher card

Two versions of the same page:

- `index.html` + `assets/`: the editable version. Images are separate files, so the HTML is short and readable. Upload the whole folder.
- `../ghosted-birds-single-file.html`: everything inlined in one file (about 3 MB). Drop it anywhere and it works.

## Hosting on GitHub Pages
Put the folder in your repository (for example `/ghosted-birds/`). Pages will serve it at `.../ghosted-birds/`. No build step is needed. Fonts load from Google Fonts.

## How the scroll works (bottom of index.html)
- Each name and drab bird has a `data-t` value: its final strength, from 0.12 + 0.88 × ln(papers + 1) ÷ ln(598), or 0 for no papers.
- Everything loses strength at the same rate as you scroll; each element stops at its own `data-t`.
- `K = 0.4933` is the ink strength of a name at the top of the scale (calibrated to match the Photoshop file's 62% layer and Brightness/Contrast).
- `FADE_START` / `FADE_END` set where in the pinned section the fade happens (0 = section top, 1 = bottom). `.scrolly{height:460svh}` sets how long the section is.
- The Rufous Hummingbird and Barn Swallow have a second, boosted image on top that fades in across the scroll.

## The resizing rows
- Two rows share one script. Row A (`#rowA`) scrolls from research papers to population; row B (`#rowB`) scrolls from research papers to body size and offers all three states on its switch.
- Each `<img class="rb">` has `data-s`: its scale in each of that row's states, in order. Each label line (`.ln`) matches a state and comes forward when that state is shown.
- On each section, `data-from` / `data-to` set which states the scroll moves between, and `data-stops` sets where in the pinned section the change happens.
- Painted area is interpolated between states, and every state has the same total area. Body size uses area proportional to length squared (lengths from Cornell's All About Birds).
- The buttons pause the scroll; scrolling back above a section hands control back to the scroll. Reduced motion gives an instant switch.

## Why the Thrasher was ghosted
- **Choose a card (`#game`):** two face-down cards (the back is the ghosted opening graphic, `assets/cardback.jpg`). The order is shuffled on every deal. Choosing a card flips both, plays the seven rounds of the aesthetic score in turn, and reports whether the reader won and why. Built from the paper's aesthetic-score components (Fischer et al. 2025 data file). The pick buttons are real buttons, so the game works by keyboard and screen reader; reduced motion skips the flip.
- **Distance illustration (`#distance`):** Sarah-Jane's collage (`assets/distance.jpg`, cropped from her 2400 × 3000 file). The dotted line is an SVG path revealed by a clip rectangle as the figure scrolls up the screen; it is a gesture, not a measured distance.
- **University dots (`#unis`):** one dot per four-year college or university within the breeding range (`Num_universities`). Both panels fill at the same rate and each stops at its own count.

## Phones (under 700px wide)
- The resizing rows become a column: each bird sits in a slot as tall as it ever gets, with its label on the right showing only the current measure. Sizes are worked out in pixels from the column's height.
- After a card is chosen, only the reader's card is shown, with the opponent's value beside each stat.
- The university dot panels stay side by side.

## Adding the next section
Add new `<section>`s after `</section>` of `#scrolly`. If the next graphic also pins and scrolls, copy the `.scrolly` / `.pin` pattern and give it its own id and script.

## Attribution (AI use)
Agreed between Sarah-Jane and Claude (Anthropic) at the end of the opening-graphic web build, October 2026.

- **Ideas:** Sarah-Jane conceived the scroll as the act of ghosting and made the key design decisions: same-rate fading, the boost, birds with no papers vanishing, the bright birds staying represented, and replacing the side captions with explainers. Claude proposed the timing options she chose from, suggested putting the birds on the same formula as the names, flagged the eight names missing from the field, and suggested keeping the empty labels as a record of absence.
- **Drafting:** Claude coded the page and calibrated it against her Photoshop file.
- **Revision and voice:** Sarah-Jane directed each iteration. The explainer text is still Claude's placeholder, to be rewritten in her voice.

### Attribution for the build after the opening (AI use)
Agreed between Sarah-Jane and Claude (Anthropic), October 2026.

- **Ideas:** Sarah-Jane shaped the narrative arc and its sequence: the opening, the two resizing rows, the question about actual size, meeting the Crissal Thrasher, and the turn to "why", told from the Thrasher's side. She proposed sizing the birds by population, combining scroll and switch, cutting back to two comparisons before the body-size question, removing the findings from the introduction so the graphics carry the story, the game-card riff, the range-map overlay, and a methods note for transparency. She made the illustrations, including the ranked birds and the Oxford distance collage. Claude proposed drawing to true scale by painted area, keeping the same total area across states, the switch as the accessible control, the scorecard and university-dot graphics, and the "same rate, own stopping point" grammar for the dots. It checked the story against the paper's data: it found that shyness and distance weren't measured factors, that the Thrasher wins two scorecard rounds, the Scrub-Jay conservation question, and the Mexico coverage question.
- **Drafting:** Claude wrote all the code. It sourced body lengths from Cornell, cleaned two cut-outs, analysed the paper's dataset, and drafted the placeholder explainers and the Thrasher card text from Cornell and Audubon sources.
- **Revision and voice:** Sarah-Jane directed every iteration and made the editorial calls. The explainers and card text remain to be rewritten in her voice.

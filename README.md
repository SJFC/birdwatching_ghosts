# Birdwatching Ghosts

**An interactive, long-form infographic about birds overlooked by scientific research — and the ways in which human attention shapes what we know about the natural world.**

*Birdwatching Ghosts* draws on research by Fischer, Otten, Lindsay, Miles and Streby (2025), published in *Proceedings of the Royal Society B*, 292: 20242846 ([original paper](https://doi.org/10.1098/rspb.2024.2846) | [research data](https://doi.org/10.5061/dryad.4f4qrfjpr)).

The original study examines differences in scientific attention across 293 North American bird species over 56 years. This infographic selects ten birds to explore those differences through historical illustration, collage, animation, comparative visualisation and interaction.

The central proposition is that **research attention is not the same as abundance, ecological significance or the existence of a living creature**. Changing the way birds are represented can reveal what is emphasised, what is overlooked and how apparently objective measures reflect human choices.

The work is intended as a critical visual exploration, rather than a comprehensive representation of the original research. It invites readers to question the relationships between data, attention, visibility and knowledge.

**[View the live infographic](https://sjfc.github.io/birdwatching_ghosts/)**

Detailed sources, methodological qualifications and image credits are available in the research notes at the foot of the webpage.

## The experience

The infographic unfolds through a series of connected visual encounters.

**Ghosting and visibility.** Historical bird illustrations and their names fade according to their representation in the research literature. The resulting absences make unequal scientific attention visible.

**Changing the measure.** Ten birds are compared through research publication counts, estimated populations and physical body lengths. The same species assume very different visual prominence depending on the measure selected.

**Beauty and classification.** Comparative scorecards explore the relationship between aesthetic characteristics and research attention, before introducing an alternative, imagined system of values.

**Geography and access.** Breeding ranges and the distribution of universities are used to explore geographical proximity as another possible influence on research attention.

**Playing with value.** An interactive card game invites visitors to engage with an imagined set of bird characteristics. It extends the infographic's central question: how do the categories we choose influence what appears important?

Together, these encounters encourage the reader to move between scientific evidence, visual interpretation and critical reflection.

## Research and interpretation

The infographic uses the published findings and associated data from Fischer et al. (2025), alongside supplementary population estimates and natural-history information.

The ten featured birds are a deliberately selected subset of the original dataset and should not be treated as statistically representative of all 293 species.

Some sections use published measures; others employ artistic interpretation, exploratory comparisons or deliberately imagined scoring systems. These distinctions are explained in the accompanying research notes.

The work does not claim that research attention can be explained by any single factor, nor that a low publication count indicates a complete absence of knowledge about a species.

## Design and development

*Birdwatching Ghosts* was conceived and visually directed by Sarah-Jane Crowson, combining archival natural-history illustrations with contemporary data visualisation and interactive storytelling.

The design process involved iterative experimentation with image opacity, proportional scaling, scrolling transitions, juxtaposition and game-based interaction.

AI tools were used collaboratively to support technical implementation, critical discussion, editorial development and testing. The approach was artist-directed, with conceptual, visual and interpretive decisions made by Crowson.

## Technical notes

The site is a self-contained HTML, CSS and JavaScript project, published through GitHub Pages. It requires no build step.

### Files

- `index.html` — page structure, styling, interactive behaviour and scripts. Fonts are loaded from Google Fonts.
- `assets/` — historical engravings, bird illustrations, range-map backgrounds, flock imagery, university collage (`distance-map.jpg`) and card-back graphics.
- `assets/row/` — cropped bird illustrations used in comparative rows and playing cards.
- `distance.jpg` — an earlier collage, retained in the repository but no longer used.

### Interactive components

**Opening tree (`#scrolly`)**

Each bird name and illustration has a `data-t` value representing its final visibility:

`0.12 + 0.88 × ln(papers + 1) ÷ ln(598)`

Species with no qualifying papers have a final value of zero.

All elements fade together as the visitor scrolls, stopping at their individual target opacity. `K = 0.4933` adjusts the names' ink strength to match the original artwork. Additional images of the Rufous Hummingbird and Barn Swallow appear during the transition. The stage begins slightly enlarged and draws back as the sequence unfolds.

**Comparative resizing (`#rowA`, `#rowB`)**

Each species has `data-s` values defining its scale in different states. Painted area is interpolated between states, with total displayed area kept consistent. The body-length comparison uses area proportional to squared length.

`data-from`, `data-to` and `data-stops` control the scroll transitions. Manual buttons temporarily override scrolling; control returns to the scroll sequence when the visitor moves back above the section.

**Scorecards (`#trumps`, `#trumps2`)**

Comparative cards are revealed sequentially through scrolling.

`data-helps` stores the accompanying explanation for each round, while `data-final` on `.tally` provides the concluding text.

The first comparison uses aesthetic scores from the published research; the second introduces imagined values.

**Breeding-range visualisation (`#ranges`)**

Each bird symbol represents approximately 41,000 breeding birds.

`data-o` determines when an individual appears during scrolling, while `data-a` controls its final opacity.

**University collage (`#distance`)**

An SVG path, progressively revealed through a clipping rectangle, traces the dotted line as the collage moves through the viewport.

**University comparison (`#unis`)**

Dots represent four-year colleges and universities located within the illustrated breeding ranges.

Both panels animate at the same rate, with each stopping at its respective count.

**Interactive card game (`#vgame`)**

The game uses `data-deck` and `data-values` to define the cards and their characteristics.

Cards are shuffled and dealt into two hands of five. The visitor selects a characteristic to play; the higher score wins both cards. Drawn cards remain in the centre until the next winning round. The opposing hand selects its highest available value when making its choice.

The values form part of an imagined, interpretive system rather than a scientific classification.

### Accessibility and responsive design

Reduced-motion preferences are respected throughout, with scroll-driven animations bypassed where requested.

On screens narrower than 700px:

- Comparative rows become vertically arranged, with each bird resizing beside its label.
- Scorecards combine into a single head-to-head presentation.
- The opposing card in the interactive game displays only its chosen value.
- University collage labels move beneath the image.

## Attribution

**Concept, research interpretation, visual design, collage and creative direction:** Sarah-Jane Crowson.

**Interactive website development and technical implementation:** Claude (Anthropic), working through an iterative, artist-directed process.

**Critical dialogue, conceptual exploration, data ethics, accessibility and editorial support:** ChatGPT (OpenAI).

Fact-checking and methodological review were undertaken collaboratively, with final editorial and interpretive decisions retained by the artist.

The underlying scientific research and original analysis are the work of Fischer et al. (2025). Supplementary data, source materials and image credits are documented on the website.

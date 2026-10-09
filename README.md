Birdwatching Ghosts

A long-form scrolling infographic about birds that research has overlooked, built from Fischer, Otten, Lindsay, Miles and Streby (2025), Proceedings of the Royal Society B 292: 20242846 (paper, data).

Live at https://sjfc.github.io/birdwatching_ghosts/. Sources, methods and image credits are in the notes at the foot of the page.

Attribution

Concept, research interpretation, visual design and creative direction: Sarah-Jane Crowson.

Technical build of the website, including the interactive game; calculations for the scaled graphics; first drafts of the imagined scores and notes: Claude (Anthropic), through an iterative, artist-directed process.

Critical dialogue, data ethics and editorial support: ChatGPT (OpenAI).

Fact-checking was shared in dialogue. All creative and interpretive decisions remained with the artist.

The original research and its data analysis are the work of Fischer et al. (2025).

Files
index.html: the whole page: markup, styles and scripts. Fonts load from Google Fonts; there is no build step.
assets/: the background engraving, bird plates, range-map base and flock birds, the university collage (distance-map.jpg) and the card back. assets/row/ holds the cropped birds used in the rows and cards. distance.jpg is an earlier collage and is no longer used.
How the page works

In page order:

Opening tree (#scrolly). Each name and faded bird has a data-t value, its final strength: 0.12 + 0.88 × ln(papers + 1) ÷ ln(598), or 0 for no papers. Everything loses strength at the same rate as you scroll and stops at its own data-t. K = 0.4933 sets the names' ink strength to match the original artwork. The Rufous Hummingbird and Barn Swallow have a boosted image that fades in across the scroll. The stage starts slightly zoomed and draws back as the fade runs.
Resizing rows (#rowA, #rowB). Each bird's data-s gives its scale in each state. Painted area is interpolated between states, and every state has the same total area; body size uses area proportional to length squared. data-from, data-to and data-stops set what the scroll moves between and when. The buttons pause the scroll; scrolling back above the section hands control back.
Scorecards (.trumps: #trumps and #trumps2). One round is revealed per scroll step. data-helps holds the line shown for each round and data-final on .tally the closing line. The first uses the study's aesthetic scores; the second the imagined values.
Range map (#ranges). Each little bird stands for about 41,000 breeding birds. Each has a data-o (when it appears as you scroll) and data-a (its final opacity, paler for the northernmost swallows).
University collage (#distance). The dotted line is an SVG path revealed by a clip rectangle as the figure scrolls up the screen.
University dots (#unis). One dot per four-year college or university in each breeding range. Both panels fill at the same rate and each stops at its own count.
The game (#vgame). The deck and values live in data-deck and data-values. Cards are shuffled and dealt five each; the reader picks a value, the higher score takes both cards, draws wait in the middle for the next winner, and the other hand plays its highest value when it chooses.

Reduced-motion settings skip the animations throughout.

Phones (under 700px wide)
The resizing rows become a column, with each bird resizing beside its label.
The two scorecards merge into one head-to-head card.
In the game, the other hand's card shows only the value being played.
The collage labels sit below the picture.

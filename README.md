# Stardate Plot

An interactive timeline of every Star Trek film and every season of every Star
Trek series — 14 films and 48 seasons across 11 series — plotted on two clocks at
once: the **release date** it reached us, and the **stardate** spoken in the
captain's log.

Each season is entered at its first episode: the date that episode first aired,
and the in-universe dating of that episode.

Open `index.html` in any browser. No build step, no dependencies — one
self-contained file.

## Controls

**Show** switches between films only, TV only, and both together; everything
downstream — plot, chart, table, ranks — follows the filter. A small icon marks
each entry as a film (▯ film strip) or a TV season (▭ screen).

## Three ways to read it

- **Plot** — a proportional vertical axis. Pick a clock (release date, stardate,
  or in-universe year), and the films animate to their true positions on it.
  Where films crowd together, cards are nudged apart and joined back to their
  real tick by a leader line. *To scale* shows the real gaps; *Even* collapses
  them to a ranked list. The arrow button reverses the order.
- **Compare** — a paired-rank chart. Two clocks side by side, one line per film,
  so the reordering between them is the picture.
- **Table** — every field, sortable by any column.

Selecting a film anywhere fills the detail panel with its rank on all three
clocks, its numbering system, and any time travel the film gets up to. `Esc`
clears the selection.

## About the data

The films use three mutually incompatible stardate systems, which is why the
stardate axis behaves so strangely:

| System | Films | Shape |
| --- | --- | --- |
| TOS-era | *The Motion Picture* – *The Undiscovered Country* | four digits, no fixed rate |
| TNG-era | *Generations* – *Nemesis* | five digits, ~1000 per year, 41000 = 2364 |
| Kelvin | *Star Trek* (2009) – *Beyond* | calendar year, then day of year |

TOS, TAS and *Discovery*'s first two seasons keep four-digit logs; TNG, DS9,
*Voyager* and *Lower Decks* keep five-digit ones.

Sorted by raw stardate, the Kelvin films land *below* Kirk's — 2258 is a smaller
number than 7412 — even though they are set fifteen years earlier and were filmed
thirty years later.

23 of the 62 entries never state a stardate. Rather than inventing one, they are
drawn hollow and dashed, and on the stardate axis they drop into a tray below the
plot. A **grey** marker means the production never used stardates at all —
*Enterprise* refused them outright, and *Picard*, *Prodigy*, *Strange New Worlds*
and *Discovery*'s 32nd-century seasons followed. A **coloured but hollow** marker
means the show does keep stardates, but this particular premiere states none
(*Insurrection*, DS9 season 7).

A year shown as `c.` is inferred from the surrounding story rather than stated on
screen. Stardates are quoted as spoken. Film release dates are original US
theatrical premieres, except *Section 31*, which went straight to Paramount+.

The short-film anthologies *Short Treks* and *Very Short Treks* are left out:
their instalments have no shared season chronology to plot.

Sorting by in-universe year opens a nine-century canyon at the top of the axis,
where *Discovery*'s last three seasons sit.

## Notes on the build

- Plain HTML, CSS and JavaScript in a single file.
- Light and dark themes, following the OS setting.
- The three era colours were checked for colour-vision separation against both
  backgrounds; identity is never carried by colour alone (every card and row is
  directly labelled, and the legend is always on screen).
- Position transitions run through one `requestAnimationFrame` tween so the dots,
  cards and leader lines stay in sync; `prefers-reduced-motion` skips them.

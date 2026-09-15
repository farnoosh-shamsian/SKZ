# Places of the SKZ: geographic linking

Every place named in the trilingual inscription of Šābuhr I at the Kaʿba-ye Zartošt,
identified, linked to standard gazetteers, and mapped.

| file                               | what it is                                                                                                                                                                                                                                                           |
| ---------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [`skz-places.tsv`](skz-places.tsv) | the gazetteer: 148 places behind the 206 `#LOC` / `#LOCderiv` attestations in [`../named-entities.tsv`](../named-entities.tsv), 128 of them with coordinates                                                                                                         |
| [`skz-map.html`](skz-map.html)     | the visualisation: one self-contained file, no libraries and no network requests. Download it and open it in a browser, or view it through [htmlpreview](https://htmlpreview.github.io/?https://github.com/farnoosh-shamsian/SKZ/blob/main/geo-linking/skz-map.html) |

## The gazetteer

One row per place. `place_id` is the key; entities in `named-entities.tsv` join to it on
the Greek form plus the line number.

| column                                                                     |                                                                                                                                                                                        |
| -------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `place_id`, `label`, `type`                                                | key, modern English name, and kind of place                                                                                                                                            |
| `certainty`                                                                | `certain`, `probable`, `uncertain`, `unidentified`, `not-a-place`                                                                                                                      |
| `attestations`, `lines`                                                    | how often and in which ŠKZ lines the place is named                                                                                                                                    |
| `greek_forms`, `parthian_forms`, `mp_forms`                                | the surface forms in the three versions                                                                                                                                                |
| `pleiades_id`, `pleiades_uri`, `pleiades_title`                            | [Pleiades](https://pleiades.stoa.org)                                                                                                                                                  |
| `wikidata_qid`, `wikidata_uri`, `wikidata_label`                           | Wikidata                                                                                                                                                                               |
| `latitude`, `longitude`, `coord_source`                                    | position, and where it came from                                                                                                                                                       |
| `glossar_lemma`, `huyse_type`, `huyse_book_page`                           | the Glossar entry behind the identification, and its page. `huyse_type` is Huyse's own tag: `ON` place name, `LN` land name, `VN` name of a people, `PN` personal name, `EN` honorific |
| `huyse_verdict`, `huyse_check_note`                                        | what checking the printed page did to our record — `confirms`, `corrects`, `resolves`, `refines`, `downgrades`, `flags` — and the specific finding                                     |
| `text_flags`, `huyse_flags`, `link_flags`, `review_flags`, `action_needed` | open problems, so they are visible rather than buried                                                                                                                                  |

128 places carry coordinates. The other 20 are off the map for three different
reasons, which the map separates: Huyse names them but their localisation is disputed or
unknown; he states outright that they cannot be identified; or they are not places at all.

## Method

Identifications and localisations follow Huyse's _Griechisches Glossar_ (Band 1,
pp. 114–171), entry by entry checked automatically against the printed page, with Band 2's _Kommentar_
used for the contested cases. Places were then resolved against the full Pleiades dumps
and against every Wikidata item carrying a Pleiades ID (P1584); identifiers are never
written from memory.

**Huyse 1999 is in copyright, and this repository points to it rather than reproducing
it.** His printed Glossar wording is not included; each record carries his lemma, his
ON/LN/VN type and the book page instead. From the Kommentar these files carry only what
those sections establish — which place is meant, its modern name, his certainty wording,
the march routes, the referent corrections and the cross-references — with a section and
page for each. His prose, the argument behind each case, and his footnotes are not
reproduced. Every identification here should be checked against the book at the page given.

## AI assistance

The work in this folder — linking the OCR'd Glossar entries to the places they name,
resolving those places against open data (Pleiades and Wikidata), assembling the
gazetteer and the map, and writing the English summaries and notes — was done by
**Claude Opus 5** (Anthropic), working in Claude Code.

## Citing

F. Shamsian & M. Berti, "Annotating Named Entities in the Trilingual Inscription at
Kaʿba-ye Zartošt (ŠKZ)", _Digital Classics Online_ 12,2 (2026),
[doi:10.11588/dco.2026.12.112297](https://doi.org/10.11588/dco.2026.12.112297).

P. Huyse (ed.), _Die dreisprachige Inschrift Šābuhrs I. an der Kaʿba-i Zardušt (ŠKZ)_,
Corpus Inscriptionum Iranicarum III/I/I, London 1999.

Coastline on the map is generalised from [Natural Earth](https://www.naturalearthdata.com)
(1:50m land, public domain), embedded in the file.

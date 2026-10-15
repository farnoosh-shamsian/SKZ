# Places of the SKZ: geographic linking

Every place named in the trilingual inscription of Šābuhr I at the Kaʿba-ye Zartošt,
identified, linked to standard gazetteers, and mapped.

| file | what it is |
| --- | --- |
| [`skz-places.tsv`](skz-places.tsv) | the gazetteer: 150 places behind the 206 `#LOC` / `#LOCderiv` attestations in [`../named-entities.tsv`](../named-entities.tsv), 137 of them with coordinates |
| [`skz-map.html`](skz-map.html) | the visualisation: one self-contained file, no libraries and no network requests. Download it and open it in a browser, or view it through [htmlpreview](https://htmlpreview.github.io/?https://github.com/farnoosh-shamsian/SKZ/blob/main/geo-linking/skz-map.html) |

## The gazetteer

One row per place. `place_id` is the key; entities in `named-entities.tsv` join to it on
the Greek form plus the line number.

| column | |
| --- | --- |
| `place_id`, `label`, `type` | key, modern English name, and kind of place |
| `certainty` | `certain`, `probable`, `uncertain`, `unidentified` |
| `attestations`, `lines` | how often and in which ŠKZ lines the place is named |
| `greek_forms`, `parthian_forms`, `mp_forms` | the surface forms in the three versions |
| `pleiades_id`, `pleiades_uri`, `pleiades_title` | [Pleiades](https://pleiades.stoa.org) |
| `wikidata_qid`, `wikidata_uri`, `wikidata_label` | Wikidata |
| `latitude`, `longitude`, `coord_source`, `coord_precision` | position, where it came from, and how much it is worth saying — `point` a site you can stand on, `centroid` a notional centre for something with an extent, `approximate` a position placed by hand |
| `glossar_lemma`, `huyse_type`, `huyse_book_page` | the Glossar entry behind the identification, and its page. `huyse_type` is Huyse's own tag: `ON` place name, `LN` land name, `VN` name of a people, `BN` mountain name, `Adv.` an adverb lemma (only ἀνωτάτω, behind Abaršahr) |
| `huyse_verdict`, `huyse_check_note` | how the record stands to his printed entry — `confirms`, `corrects`, `resolves`, `refines`, `downgrades`, `flags` — and what that entry says |
| `note` | a short note on the record: what the identification turns on, or what Huyse’s entry says |
| `text_flags`, `huyse_flags`, `link_flags` | what is emended, restored or missing in the text, what Huyse marks, and what is unlinked |
| `resolution`, `n_flags` | how a disagreement with Huyse was settled, and how many flags the record carries |

137 places carry coordinates. The map separates the other 13 by why they are off it:
Huyse names them but their localisation is disputed or unknown, or he states outright that
they cannot be identified.

Each identification is referred to the page of the Glossar it rests on, and where it and
Huyse's entry differed, his reading was adopted - see the `huyse_verdict`,
`huyse_check_note` and `resolution` columns.

## Method

Identifications and localisations follow Huyse's *Griechisches Glossar* (Band 1,
pp. 114–171), entry by entry, with Band 2's *Kommentar* for the contested cases. Places
were then resolved against the full Pleiades dumps and against every Wikidata item
carrying a Pleiades ID (P1584), so that every identifier in the table comes from those
sources rather than from a guess at the number.

**Huyse 1999 is in copyright, and this repository points to it rather than reproducing
it.** His printed Glossar wording is not included; each record carries his lemma, his
ON/LN/VN type and the book page instead. From the Kommentar these files carry only what
those sections establish — which place is meant, its modern name, his certainty wording,
the march routes, the referent corrections and the cross-references — with a section and
page for each. His prose, the argument behind each case, and his footnotes are not
reproduced. Every identification here can be checked against the book at the page given.

## Open-weight models on the same task

The layer was built with Claude Opus 5 (see the note on AI on the
[landing page](https://farnoosh-shamsian.github.io/SKZ/)). Two open-weight models,
gpt-oss-120b and gpt-oss-20b, were tested on one step of that work: given the text of a
Glossar entry, report its type, the modern name, and how certain Huyse is.

Both matched Huyse's type almost every time. They gave the modern name for 91% and 84% of
the entries that have one, and left it out for the rest. On certainty they did little
better than answering "certain" every time (75% against 73%): of the 39 entries Huyse
hedges, each got 6 right and called 17 certain, five of them entries he says cannot be
identified.

Reading the entries from the page images and linking places to Pleiades have not been
tested with an open-weight model.

## Citing

F. Shamsian & M. Berti, "Annotating Named Entities in the Trilingual Inscription at
Kaʿba-ye Zartošt (ŠKZ)", *Digital Classics Online* 12,2 (2026),
[doi:10.11588/dco.2026.12.112297](https://doi.org/10.11588/dco.2026.12.112297).

P. Huyse (ed.), *Die dreisprachige Inschrift Šābuhrs I. an der Kaʿba-i Zardušt (ŠKZ)*,
Corpus Inscriptionum Iranicarum III/I/I, London 1999.

Coastline on the map is generalised from [Natural Earth](https://www.naturalearthdata.com)
(1:50m land, public domain), embedded in the file.

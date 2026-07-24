# Walking the Talk

A searchable archive of confirmed sites from Frederick Douglass's 1846 lecture tour of Scotland — every location rated by how sure we actually are, sourced back to newspapers, digitized archives, and primary transcripts.

**[Live site →](#)** *(add your GitHub Pages URL here once deployed)*

## Why this exists

Most online material about Douglass's time in Scotland is either a scholarly deep-dive (hard to browse) or a tourist-trail summary (light on sourcing, occasionally wrong). This project tries to sit between the two: browsable, searchable, and honest about confidence level, with every claim traceable to a source.

A guiding principle: **it's fine if this isn't a clean, tidy narrative.** Douglass's actual itinerary zigzagged, some claims about it online are simply wrong (see the Scottish Borders entry), and some buildings survive while others don't. The site should reflect that mess accurately rather than smooth it over.

## Structure

```
douglass-archive/
├── index.html          # the whole app — search, filters, rendering
├── data/
│   └── entries.json     # the actual dataset — edit this to add/change entries
└── README.md
```

The dataset is deliberately separated from the page logic so it can grow without touching any code.

## Running locally

Because `index.html` fetches `data/entries.json`, most browsers will block it if you just double-click the file (the `file://` protocol blocks local JSON fetches). Run a tiny local server instead:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## Adding or editing an entry

Each object in `data/entries.json` follows this shape:

```json
{
  "name": "Location name",
  "cat": "lodging | venue | transit | transcript",
  "city": "City",
  "date": "Date or date range as it appears in sources",
  "conf": "confirmed | probable | disputed",
  "body": "1-3 sentences, in your own words, summarizing what's confirmed.",
  "note": "(optional) A caveat, discrepancy, or 'here's what doesn't line up' note.",
  "source": "Short citation — publication or site name",
  "url": "Link to the source",
  "linkLabel": "Text for the outbound link"
}
```

### Confidence levels — use them honestly

- **confirmed** — a primary source (contemporary newspaper report, published transcript, archival letter) directly places Douglass at this location on this date.
- **probable** — reasonably well-attested (named by Douglass himself, or by a specialist secondary source) but not independently verified against a primary account.
- **disputed** — actively circulating online but contradicted or unconfirmed by the best available source. Keep these in the archive rather than deleting them — flagging a wrong claim is more useful to future researchers than silently omitting it.

### A note on copyright

Do not paste full newspaper transcripts or lengthy verbatim quotes into `body` or `note` — summarize in your own words and link to the original source instead. Short quotes (a few words) with clear attribution are fine.

## Roadmap / not yet built

- Map view (the historic-overlay work already done for this project used the National Library of Scotland's georeferenced map viewer — see maps.nls.uk/geo/explore/side-by-side/)
- Inline full-text panels for the primary-source transcripts (currently just linked out to frederickdouglasspapersproject.com)
- Expansion beyond Scotland to the rest of the 1845-47 British and Irish tour

## Core sources

- Frederick Douglass Papers Project — digital edition (frederickdouglasspapersproject.com)
- National Library of Scotland — georeferenced historic maps (maps.nls.uk)
- Alasdair Pettinger, "Frederick Douglass in Scotland" (bulldozia.com)
- Glasgow Life / Glasgow Museums — "Legacies of Slavery and Empire"
- Historic Environment Scotland

## License

Code in this repository (`index.html` and associated JS/CSS) is available under the MIT License — see `LICENSE`.

The dataset in `data/entries.json` is original summary/citation text written for this project, not reproduced from sources — but always verify against the linked primary source before treating an entry as authoritative. This is a working document, not a finished scholarly record.

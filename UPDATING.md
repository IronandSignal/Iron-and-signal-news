# Weekly update rules (Industry News)

The Iron & Signal site (ironandsignal.com/industry-news) loads `news.json` from this repo on every page view.
Updating the page = editing `news.json` and pushing to `main`. The site picks it up within ~5 minutes.

## news.json format

```json
{
  "week": "Week of Nov 9, 2026",
  "updated": "2026-11-09",
  "stories": [
    {
      "category": "Construction",
      "url": "https://...",
      "image": "1503708928676-1cb796a0891e",
      "text": "One sentence in our own words.",
      "source": "ENR",
      "date": "Nov 6"
    }
  ]
}
```

- `week`: "Week of <this Monday, Mon D, YYYY>".
- Exactly 9 stories, in this order: 3 Construction / Heavy Civil, then 3 Geospatial, then 3 Mining.
- `category`: one of `Construction`, `Heavy Civil`, `Geospatial`, `Mining`.
- `url`: must start with `https://` and be a real article from the search results.
- `image`: the Unsplash ID only (the part after `photo-` in an `images.unsplash.com/photo-<ID>` URL). It must match `^[0-9]+-[0-9a-f]+$`, or the page drops the image.
- `text`: one sentence in our own words, under about 25 words. No copied phrasing.
- `date`: short format, like "Nov 6".
- Plain text only, no HTML. The page escapes it.

## Sources

Use the biggest trade and news outlets, and stories from the last 7 days.

- **Construction / Heavy Civil:** ENR, Construction Dive, Equipment World, For Construction Pros, Construction Equipment Guide, Rock Products, FMI, AGC/Census data.
- **Geospatial:** Geo Week News, GPS World, xyHt, Inside GNSS, Trimble/Hexagon/Topcon IR.
- **Mining:** MINING.COM, Mining Weekly, International Mining, Northern Miner, Mining Magazine.

Prefer:
- earnings for CAT, Deere, Komatsu, Volvo CE, Trimble, Hexagon and the major miners
- big contracts
- M&A
- market data
- major launches

## Hard rule

**No Teledyne.** No stories about Teledyne or any Teledyne brand or product: CARIS, PDS, RESON, Optech, Teledyne Geospatial, FLIR, etc.

## Images

- Use a free Unsplash photo that fits each story, such as an excavator, highway work, a surveyor on a tripod, an aerial city view, an open-pit mine or gold bars.
- To get an ID:
  1. Search with `site:unsplash.com <topic>`.
  2. WebFetch the photo page.
  3. Read the `images.unsplash.com/photo-<ID>` main image URL. Ignore the og:image overlay.
- Never use a publisher's own article photos.
- If you can't get a fresh ID, reuse one from `image-pool.json` for that category. Add any new IDs you used to the pool.

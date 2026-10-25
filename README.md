# Kulturbiblioteket Vinyl Finder

A searchable catalogue of the ~15,000 vinyl records you can borrow at [Kulturbiblioteket](https://kulturhusetstadsteatern.se/lana-hem-vinyl) in Kulturhuset Stadsteatern, Stockholm.

**Live:** https://pnettto.github.io/kh-vinyls/

- `index.html`: browse as a cover wall or list, with search and genre, year and country filters
- `stats.html`: charts about the collection
- `data.js`: the catalogue, built from the library's PDF lists
- `covers/`: cover images from the library and MusicBrainz

## Where the data comes from

All the data comes from public sources, and each record links back to where it came from.

- **The library's own lists.** Kulturbiblioteket publishes its vinyl collection as 13 PDF lists, split by section: pop/rock, jazz & blues, classical, folk & world, film music, popular music & visor, and spoken word. Each list is parsed record by record. The spoken-word list is a scanned image, so it was typed in by hand. Every record links to its page in the original PDF.
- **The Stockholm Public Library catalogue.** Newer vinyl that isn't in the PDFs comes from the catalogue at [biblioteket.stockholm.se](https://biblioteket.stockholm.se). These records link to their catalogue page.
- **Requests are polite.** All harvesting is rate-limited and caches its results, so each source is only asked once.

## What was added

The lists give an artist, a title and sometimes a year. To make the collection browsable, three things were added, and the site always shows which parts are confirmed and which are inferred.

### Genres

- Every record gets genres from a fixed set of 62, grouped into nine families such as Rock, Jazz, Classical and Folk & world. Swedish traditions like *visor* and *schlager & dansband* have their own genres.
- **Classical records are tagged by rules, not AI.** The form (symphony, concerto, opera, chamber music and so on) comes from keywords in the work titles. The era (baroque, romantic and so on) comes from the composer's birth year in the catalogue heading.
- **All other records are tagged by a language model.** It was told to rely on what it actually knows about the artist and album, and to say when it is only inferring. Several models were compared on a sample before one was chosen.
- About 2,000 records have genres marked as guesses. On the site these appear dashed, with a "?", and a toggle hides them from filters.

### Countries

- **Folk & world:** countries come straight from the library's lists, which are already organised by region and country. Swedish place names are translated to English.
- **Everything else:** the country is where the main artist comes from, or the composer for classical. A language model inferred it under the same rules as for genres. About 600 records with an uncertain country are marked with a "?" and can be filtered out.

### Covers

- 3,786 records have a cover.
- **From the library:** covers for the newer vinyl come from the library catalogue.
- **From open music data:** the rest come from [MusicBrainz](https://musicbrainz.org), the open music encyclopedia, and its [Cover Art Archive](https://coverartarchive.org).
  - To avoid putting load on their servers, matching runs against MusicBrainz's public data dump instead of their live API.
  - A cover is used only when both the artist and the title closely match. Otherwise the record shows a plain printed sleeve, not a cover that might be wrong.

## Running it

It's a static site with no build step. To run it locally, open `index.html` or run `python3 -m http.server`.


## About

This is an independent, non-commercial project made to help people discover the library's vinyl collection. It is not affiliated with Kulturhuset Stadsteatern or Stockholms stadsbibliotek. Cover images belong to their respective rights holders. If you'd like something changed or removed, please [open an issue](https://github.com/pnettto/kh-vinyls/issues).

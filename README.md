# Kulturbiblioteket Vinyl Finder

A searchable catalogue of the ~15,000 vinyl records you can borrow at [Kulturbiblioteket](https://kulturhusetstadsteatern.se/lana-hem-vinyl) in Kulturhuset Stadsteatern, Stockholm.

**Live:** https://pnettto.github.io/kh-vinyls/

- `index.html`: browse as a cover wall or list, with search and genre, year and country filters
- `stats.html`: charts about the collection
- `data.js`: the catalogue, built from the library's PDF lists
- `covers/`: cover images from the library and MusicBrainz

It's a static site with no build step. To run it locally, open `index.html` or run `python3 -m http.server`.

To rebuild the data, including the genre, country and cover enrichment, see [`build/README.md`](build/README.md).

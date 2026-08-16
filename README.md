# fotopage

Photo gallery website of Antoine Boniface, built with [Jekyll](https://jekyllrb.com/), [lightGallery](https://www.lightgalleryjs.com/) and [Isotope](https://isotope.metafizzy.co/). Based on [jekyll-image-gallery-example](https://github.com/opieters/jekyll-image-gallery-example) by Olivier Pieters.

## Run locally

```bash
bundle install            # first time only
bundle exec jekyll serve
```

Then open <http://localhost:4000/fotopage/> (the `/fotopage/` suffix is required because of `baseurl`). Restart the server after editing `_config.yml`.

## Photos are not in the repository

`assets/photography/` is listed in `.gitignore`: the photos only exist locally and are **not** committed. Keep a backup of that folder — git does not protect it. It also means a plain GitHub Pages build from this repository will have no images; the photos must be uploaded to the web server (or added back to the repository) separately.

## Add a new gallery

A gallery named `my-trip` needs three things:

1. **Images** in `assets/photography/my-trip/` (local only, see above). Each photo needs:
   - the original: `IMG-001.jpg`
   - a thumbnail: `IMG-001-thumbnail.jpg` (used in the grid), e.g. `sips -Z 1224 IMG-001.jpg --out IMG-001-thumbnail.jpg`
   - responsive sizes: `IMG-001-2784x1856.jpg`, … — the name must end in `-WIDTHxHEIGHT.jpg` (the width is parsed from the filename), e.g. `sips -Z 2784 IMG-001.jpg --out IMG-001-2784x1856.jpg`

2. **A data file** `_data/galleries/my-trip.yml` listing the pictures (copy an existing one as a template):

   ```yaml
   picture_path: my-trip
   pictures:
   - filename: IMG-001
     original: IMG-001-6000x4000.jpg
     sizes:
     - IMG-001-2121x1414.jpg
     thumbnail: IMG-001-thumbnail.jpg
     title: Optional caption title
     caption: Optional longer caption
   ```

   Also add an entry to `_data/galleries/overview.yml` so it appears on the galleries page.

3. **A page** `photography/my-trip.md`:

   ```markdown
   ---
   layout: gallery
   title: My Trip
   support: [jquery, gallery]
   ---

   Optional intro text.

   {% include gallery-layout.html gallery=site.data.galleries.my-trip %}
   ```

## License

The code is licensed under the MIT license (see `LICENSE-CODE.md`). All photographs are © Antoine Boniface, all rights reserved.

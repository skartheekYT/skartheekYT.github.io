# Agentic AI Notes

Quarto website. Preview locally with `quarto preview`; build with `quarto render` (output in `_site/`).

## Layout

```
index.qmd      home (intro + 3 latest articles)
series.qmd     one card per series (lists series/*/index.qmd)
articles.qmd   every main article, newest first (lists series/*/*/index.qmd)
about.qmd
series/<series-slug>/
  index.qmd                 series landing page, lists its parts by `part`
  NN-<article-slug>/
    index.qmd               the article (the only file that shows up in listings)
    <companion>.qmd         companion/derivation pages, linked from the article
    <images>
```

## Adding an article to an existing series

1. Create `series/<series>/NN-<slug>/index.qmd` (NN = next part number, zero-padded).
2. Front matter:
   ```yaml
   title: "..."
   description: "..."
   date: YYYY-MM-DD
   series: "Foundations of LLMs"
   part: 4
   categories: [lowercase, hyphenated-tags]
   draft: false
   ```
3. Add it to that series' sidebar in `_quarto.yml` (as a `section:` with any companions under `contents:`).

## Adding a companion page

Put it in the article's folder, title it `"Companion: ..."`, use `series: ...` and `companion: true` (no `part`). Link to it from the article and add it under the article's sidebar section. Companions are never listed on Series/Articles/Home because the listings only pick up `index.qmd` files.

## Starting a new series

1. Create `series/<new-slug>/index.qmd` (copy the Foundations one; it holds the intro and the ordered parts table).
2. Add a new sidebar block with `id: <new-slug>` in `_quarto.yml`.
3. The series card appears on the Series page automatically.

## Moved pages

Articles used to live under `posts/`. Each moved page has `aliases:` so the old URLs redirect. Keep them.

# Paper figures

One figure per paper, shown beside the entry on `/publications/`.

> **Currently switched off.** `paper_figures` in `_config.yml` is `false`, so
> no figure column is rendered anywhere. Set it to `true` to bring it back —
> the images here and the captions in `_data/publications.yml` are kept, so
> that one line is the only change needed.
>
> Working papers never show figures, whatever that setting is.

## Adding a figure

1. Export the figure as **PNG** (or SVG). Aim for roughly **1200 px wide**;
   it is displayed at 220 px, so anything wider is wasted bytes.
   A 16:10-ish aspect ratio fits the column best.
2. Save it here with a short lowercase name, e.g. `acglobal.png`.
3. Point the paper at it in `_data/publications.yml` or
   `_data/working_papers.yml`:

   ```yaml
   figure: "acglobal.png"
   figure_alt: "Projected global residential cooling electricity demand to 2050"
   figure_caption: "Projected global residential cooling electricity reaches 976–1393 TWh by 2050."
   ```

Until `figure:` is filled in, the site shows a neutral "Figure to come"
placeholder of the same size, so the layout does not move when you add
the real image.

`figure_alt` is read aloud by screen readers — describe what the figure
shows. `figure_caption` is the visible line underneath.

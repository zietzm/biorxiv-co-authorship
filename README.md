# BioRxiv co-authorship network

This repository houses a network of all co-authorship relations from papers on [bioRxiv](http://biorxiv.org) up to March 23, 2019, including date of publication and corresponding DOI and URL. All papers have basic metadata stored in `articles.json`, in the following format:

```json

[
  {
    "date": "YYYY/MM/DD",
    "authors": [
      [
        "LAST",
        "FIRST"
      ], ...
    ],
    "url": "https://doi.org/10.1101/BIORXIV_ID"
  }, ...
]

```

Paper authors are then given unique numerical IDs, and all co-author relationships (the network itself) are stored in `biorxiv_coauthor.tsv.xz`, in the following format: [`id_a`, `id_b`, `year`]. This format means that author pairs with multiple co-authorships will have all existing co-authorships in the network. The rationale for this decision is so that the network can be time-resolved later. Note, "authors" in the context of this repository includes only individuals, meaning consortia and named groups are excluded from the network.

If you require further metadata for each paper, such as title or abstracts, I recommend using the DOIs and the [CrossRef API](https://github.com/CrossRef/rest-api-doc). DOI extraction from the URLs is simple, and is done in `2.construct_edges.ipynb` using the following regex: `'10.1101/[0-9]+'`.

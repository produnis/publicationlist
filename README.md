# publicationlist

This repository contains a [quarto](https://quarto.org) extension designed to generate a publication list from a BibTeX file, producing a PDF output (this extension uses LaTeX document class "`moderncv`". A quarto extension for generating CVs is provided here: <https://github.com/produnis/quarto-cv>).

![](https://www.produnis.de/blog/posts/2021-04-19-publikationsliste-im-lebenslauf-mit-latex/publikationslebenslauf.png)


## Installation

To use this extension, execute the following command:

`quarto use template produnis/publicationlist`


## Usage

This Quarto template takes a BibTeX file (e.g., `literatur.bib`) and generates a publication list. Examine the provided `literatur.bib` for reference.

### BibTeX file

Follow these steps:

- Organize your publications in [Zotero](https://www.zotero.org)
- Utilize the "Tags" tab in Zotero to categorize entries as journal articles, book chapters, or "gray literature." This categorization is essential for later differentiation in the publication list.
- Export the literature entries from Zotero as a "Bibtex" file (e.g., `literatur.bib`).
- Example Bibtex file structure:

```
@article{hastig1,
    title = {Regressionsmodelle für ordinale {Zielvariablen}},
    volume = {10},
    issn = {1860-9171},
    language = {de},
    number = {1},
    journal = {Journal der Zahlenkunde},
    author = {Hastig, Alber and Thefrog, Kermit},
   author+an = {1=highlight},
  year = {2014},
    keywords = {auswahl, journal, peer-reviewed},
    pages = {1--9}
}

@article{hastig2,
    title = {Warum bin ich so muede?},
    volume = {27},
    language = {de},
    number = {4},
    urldate = {2018-10-25},
    journal = {Journal der rhetorischen Fragen},
    author = {Schlappmann, Michael and ZuSpaet, Carmen and Hastig, Albert},
   author+an = {3=highlight},
  month = aug,
    year = {2014},
    keywords = {auswahl, journal, peer-reviewed},
    pages = {269--277}
}
```
Note the inclusion of keywords (tags) in each entry.

- Manually add the line  `author+an = {2=highlight}` to each author entry in the Bibtex file. This informs Quarto about your name's position in the author list (2 in this example), allowing it to highlight your name in bold during  `.tex` conversion. Though optional, this step enhances the presentation.

### YAML

In the YAML header, under the `publikationen` parameter, create a list entry for each keyword you wish to print. Specify the `key` as the keyword and `title` as the corresponding heading for that list. The example below illustrates printing four publication lists (for keywords "journal," "buch," "buchkapitel," and "konferenz"):

```
publikationen:
  - list:
      key: journal
      title: Zeitschriftenartikel (peer-reviewed)
  - list:
      key: buch
      title: Bücher   
  - list:
      key: buchkapitel
      title: Buchkapitel
  - list:
      key: konferenz
      title: Konferenzbeiträge (peer-reviewed) 
```

You can edit the `moderncv` options in YAML with parameters

```
---
moderncvtheme: casual # classic #casual
cvoption: red  # green, red, orange, grey
---
```
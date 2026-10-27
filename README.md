# That Card App data

Word lists and example sentences used by That Card App. The app downloads them after install instead of bundling
them, because they are derived from Wiktionary and Tatoeba and have to be shared under their licenses.

Two kinds of data live here, under two different licenses:

| Folder | What | License |
|---|---|---|
| repository root | Dictionaries, derived from Wiktionary | [CC BY-SA 4.0](LICENSE) |
| `sentences/` | Example sentence packs, from Tatoeba | [CC BY 2.0 FR](https://creativecommons.org/licenses/by/2.0/fr/) |

`manifest.json` lists every file with its size, entry counts, license and SHA-256 checksum, so a client can check a download.

## Dictionaries

| File | Direction | Entries (first / second section) | Size | Built from |
|---|---|---|---|---|
| `dict.txt.gz` | ru → en, then en → ru | 44,969 / 49,158 | 1.2 MB | English Wiktionary, Russian entries |
| `dict-ru-es.txt.gz` | ru → es, then es → ru | 24,549 / 28,317 | 0.6 MB | Russian Wiktionary and Spanish Wiktionary |
| `dict-en-es.txt.gz` | es → en, then en → es | 79,094 / 77,486 | 1.5 MB | English Wiktionary, Spanish entries |
| `dict-en-fr.txt.gz` | fr → en, then en → fr | 63,647 / 70,387 | 1.3 MB | English Wiktionary, French entries |
| `dict-en-de.txt.gz` | de → en, then en → de | 70,621 / 71,742 | 1.6 MB | English Wiktionary, German entries |
| `dict-en-it.txt.gz` | it → en, then en → it | 104,109 / 91,226 | 1.9 MB | English Wiktionary, Italian entries |
| `dict-en-he.txt.gz` | he → en, then en → he | 9,591 / 17,473 | 0.3 MB | English Wiktionary, Hebrew entries and English translation tables |
| `dict-ru-he.txt.gz` | he → ru, then ru → he | 7,610 / 10,463 | 0.2 MB | Russian Wiktionary, Hebrew entries and Russian translation tables |
| `dict-en-zh.txt.gz` | zh → en, then en → zh | 56,285 / 63,357 | 1.6 MB | English Wiktionary, Chinese entries (simplified characters) |

Plain text, gzip-compressed, UTF-8. Each file has two sections separated by a form-feed line (`\n\f\n`).
Each line is `word<TAB>translation1|translation2|translation3`, best translation first, up to three per word.
The first section goes from the first language to the second, the second section goes back.
Entries can be single words or short phrases such as "fall in love".

Hebrew is written without vowel points, as Tatoeba writes it. A verb is listed by its infinitive (לקרוא for "to read"), as the translations are;
Wiktionary itself lists verbs under the third person masculine past (קרא), which is kept for nouns and the like (ספר "book" and ספר "he counted" are two entries: ספר and לספור).
Chinese words are in simplified characters; Wiktionary keeps most definitions under the traditional spelling, so they were mapped back to the simplified one,
and the few traditional characters left (強, 尋, 幹 ...) were removed with their words and sentences (`tools/drop_trad_zh.py` in the app repo).

## Sentence packs

| File | Languages | Sentence pairs | Size |
|---|---|---|---|
| `sentences/sent-en-es.txt.gz` | en / es | 189,802 | 7.1 MB |
| `sentences/sent-en-fr.txt.gz` | en / fr | 225,115 | 8.3 MB |
| `sentences/sent-en-de.txt.gz` | en / de | 198,537 | 7.7 MB |
| `sentences/sent-en-it.txt.gz` | en / it | 216,932 | 6.6 MB |
| `sentences/sent-en-he.txt.gz` | en / he | 115,029 | 4.1 MB |
| `sentences/sent-ru-he.txt.gz` | ru / he | 67,540 | 2.5 MB |
| `sentences/sent-en-zh.txt.gz` | en / zh | 53,918 | 2.0 MB |
| `sentences/sent-ru-en.txt.gz` | ru / en | 417,477 | 17.7 MB |
| `sentences/sent-ru-es.txt.gz` | ru / es | 80,096 | 3.9 MB |

See [sentences/README.md](sentences/README.md) for the format and the changes made.

Download any file directly, for example:

```
https://raw.githubusercontent.com/ysevastianov/that_card_app_dictionaries/main/dict-en-es.txt.gz
https://raw.githubusercontent.com/ysevastianov/that_card_app_dictionaries/main/sentences/sent-en-es.txt.gz
```

## Attribution

**Dictionaries.** Derived from Wiktionary (https://www.wiktionary.org) by its contributors, using the structured
extracts published by kaikki.org (https://kaikki.org), which are produced with wiktextract.
Wiktionary text is available under the Creative Commons Attribution-ShareAlike 4.0 license.

**Sentences.** From Tatoeba (https://tatoeba.org), by its contributors, licensed under CC BY 2.0 FR.
The dictionary forms listed in the packs were looked up with the Wiktionary-derived data above, so credit Wiktionary too if you reuse them.

Wiktionary, the Wikimedia Foundation and Tatoeba do not endorse this project.
If you use these files, credit the sources, link the license, and say that the data was changed.
Anything you build from the dictionaries has to be shared under CC BY-SA 4.0.

## Changes made to the Wiktionary data

- Kept the first gloss of each meaning and cut each entry to at most three translations.
- Removed inflected forms, obsolete, archaic, rare, dated, dialectal, vulgar and offensive meanings, and long
  descriptions that are not translations.
- Reordered translations by how often a word occurs in Wiktionary's own example sentences and by how early it
  appears in its entry, so the most common translation comes first.
- Merged both directions into one file per language pair, and for Russian with Spanish topped up each direction
  from the other Wiktionary.
- Converted everything to the compact text format above.

## License

The dictionaries in the repository root are licensed under [CC BY-SA 4.0](LICENSE).
The full legal text is in the `LICENSE` file and at https://creativecommons.org/licenses/by-sa/4.0/legalcode.
The sentence packs in `sentences/` are licensed under CC BY 2.0 FR, see `sentences/README.md`.

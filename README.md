# That Card App dictionaries

Word lists used by That Card App. The app downloads them after install instead of bundling them, because they are
derived from Wiktionary and have to be shared under the same license.

## Files

| File | Direction | Entries (first / second section) | Size | Built from |
|---|---|---|---|---|
| `dict.txt.gz` | ru → en, then en → ru | 44,969 / 49,158 | 1.2 MB | English Wiktionary, Russian entries |
| `dict-ru-es.txt.gz` | ru → es, then es → ru | 24,549 / 28,317 | 0.6 MB | Russian Wiktionary and Spanish Wiktionary |
| `dict-en-es.txt.gz` | es → en, then en → es | 79,094 / 77,486 | 1.5 MB | English Wiktionary, Spanish entries |
| `dict-en-fr.txt.gz` | fr → en, then en → fr | 63,647 / 70,387 | 1.3 MB | English Wiktionary, French entries |
| `dict-en-de.txt.gz` | de → en, then en → de | 70,621 / 71,742 | 1.6 MB | English Wiktionary, German entries |
| `dict-en-it.txt.gz` | it → en, then en → it | 104,109 / 91,226 | 1.9 MB | English Wiktionary, Italian entries |

`manifest.json` lists every file with its size, entry counts and SHA-256 checksum, so a client can check a download.

## Format

Plain text, gzip-compressed, UTF-8. Each file has two sections separated by a form-feed line (`\n\f\n`).
Each line is `word<TAB>translation1|translation2|translation3`, best translation first, up to three per word.
The first section goes from the first language to the second, the second section goes back.
Entries can be single words or short phrases such as "fall in love".

Download one file directly, for example:

```
https://raw.githubusercontent.com/ysevastianov/that_card_app_dictionaries/main/dict-en-es.txt.gz
```

## Attribution

The dictionary data is derived from Wiktionary (https://www.wiktionary.org) by its contributors, using the
structured extracts published by kaikki.org (https://kaikki.org), which are produced with wiktextract.
Wiktionary text is available under the Creative Commons Attribution-ShareAlike 4.0 license.
Wiktionary and the Wikimedia Foundation do not endorse this project.

If you use these files, credit Wiktionary and kaikki.org, link the license, and say that the data was changed.
Anything you build from them has to be shared under the same license.

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

The files in this repository are licensed under [CC BY-SA 4.0](LICENSE).
The full legal text is in the `LICENSE` file and at https://creativecommons.org/licenses/by-sa/4.0/legalcode.

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
The Chinese dictionary file has a third section after the two translation sections: `word<TAB>pinyin` (tone marks, syllables of a longer word separated only where Wiktionary does), for every dictionary word, every word of the sentence pack, the HSK words and every single character they use (pinyin from the Wiktionary pronunciations, CC BY-SA 4.0; the usual reading of a single character from Unihan, Unicode licence).
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

## Quick start sets

`levels/level-xx.txt.gz` (listed in `manifest.json` with `kind: levels`) is the Quick start set of one learnt language: 30 words, 15 verbs (`@g=v`) and 15 travel words (`@g=t`), one per line.
A line is the headword, then extra tab-separated fields: the hand-checked translations into every language that can learn from the list (`@en=`, `@ru=`, `@es=`, `@fr=`, `@de=`, `@it=`; several meanings with `|`, best first) and the theme.
The app shows these as a set of words with two tags, the theme and `quick start`, written in the language of the learner; the translation on the card is the one in the file.
The words are chosen out of the beginner word lists below by `tools/quick_start.py` and built by `tools/build_levels.py` in the app repo; the source lists are not published here, only these 30 words per language.

| File | Chosen from | Words |
|---|---|---|
| `level-zh` | HSK 3.0 level 1 (Chinese Proficiency Grading Standards for International Chinese Language Education, 2021), as typed up in github.com/elkmovie/hsk30 (MIT) | 30 |
| `level-de` | Goethe-Zertifikat A1: Start Deutsch 1, Wortliste (Goethe-Institut) | 30 |
| `level-es` | Instituto Cervantes, Plan curricular (PCIC), A1 inventories | 30 |
| `level-it` | Profilo della lingua italiana, A1 word list (Spinelli and Parizzi, Universita per Stranieri di Perugia) | 30 |
| `level-en` | The Oxford 3000 (Oxford University Press), entries tagged A1 | 30 |
| `level-he`, `level-fr`, `level-ru` | hand-made lists of basic words (`tools/he_aleph.tsv`, `fr_top300.tsv`, `ru_top300.tsv`); there is no usable open list for them | 30 |

The first five source lists are published by their institutions, whose copyright stays with them; the files here contain only 30 headwords of each with our own translations.
The translations were written one by one for the beginner sense of each word (club is a club, not a stick) and are in `tools/levels_tr/` in the app repo.

### Order of the meanings
Wiktionary lists the meanings of a word in the order of its senses, which is not the order of use (for club the first sense is the heavy stick, for bank the river bank).
Two steps fix the order of the first meaning in the dictionaries (`tools/rerank_dict.py` and `tools/pin_level_translations.py` in the app repo):
1. For the European pairs, a meaning that occurs clearly more often than the first one in the Tatoeba sentence pairs of the pack (the word in one sentence, the meaning in its translation: at least 3 sentences and more than 1.5 times the first meaning's count) moves to the front.
   About 1 to 2 percent of the entries change.
2. The hand-checked translations of the level lists (see Quick start sets) are put in front of the entry's meanings, and a level word the dictionary lacks gets an entry.
The Hebrew dictionaries get the same two steps in their own builder (`build_dict_he.py`).

## License

The dictionaries in the repository root are licensed under [CC BY-SA 4.0](LICENSE).
The full legal text is in the `LICENSE` file and at https://creativecommons.org/licenses/by-sa/4.0/legalcode.
The sentence packs in `sentences/` are licensed under CC BY 2.0 FR, see `sentences/README.md`.

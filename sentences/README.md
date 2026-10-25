# Sentence packs

Example sentence pairs for the "missing word" practice in That Card App, one file per language pair.

## Source and license

The sentences come from Tatoeba (https://tatoeba.org), written and translated by its contributors, and are licensed under
the Creative Commons Attribution 2.0 France license (CC BY 2.0 FR): https://creativecommons.org/licenses/by/2.0/fr/

Credit line to use: **Sentences: Tatoeba**. Tatoeba does not endorse this project.

The dictionary forms listed in each line were looked up with the Wiktionary-derived dictionaries in the repository root
(CC BY-SA 4.0), so credit Wiktionary too if you reuse them.

## Format

Plain text, gzip-compressed, UTF-8, one pair per line, six tab-separated columns:

1. sentence in the first language
2. sentence in the second language
3. dictionary words of sentence 1 by word position: `3` means word 3 is already in dictionary form,
   `1:книга` means word 1 is a form of the dictionary word `книга`
4. the same for sentence 2
5. share of known words in sentence 1, in percent
6. share of known words in sentence 2, in percent

## Changes made to the Tatoeba data

- Kept a pair when one side has 3 to 15 words, contains only letters and . , ! ? ¿ ¡, and at least 60 percent of its
  words are in that language's dictionary.
- Dropped pairs with vulgar or offensive words, and pairs about sensitive topics: violence, weapons, war, terrorism,
  death, crime, drugs, sex, hate and religion. This removed about 3 percent of pairs.
- Added the dictionary-word columns and known-word percentages described above.

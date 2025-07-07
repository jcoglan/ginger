# ginger

This is a set of tools I am using to play the game
[Ginger](https://store.steampowered.com/app/3418910/Ginger/). It contains a text
copy of the in-game dictionary, the inputs for each speech sound, and a tool for
searching the dictionary. The search tool requires
[Node.js](https://nodejs.org/) to run.

The search tool can be invoked by running `./search` with any of the following
options:

- `-d WORD`: find entries that define `WORD`
- `-u WORD`: find entries that make use of `WORD`
- `-t TYPE`: find entries with definitions of type `TYPE`
- `-T`: list all word types with their frequencies
- `-s count`: sorts the results by how many definitions the word is used in,
  rather than the default alphabetical order
- `-x`: apply translations from `translations.txt` to the output

The `-d` and `-u` options can be used multiple times to search on several terms
at once. They also support pattern matching, wherein `WORD` can take the
following forms:

- `STR`: searches for an exact match on `STR`
- `X.Y`: matches words that begin with `X` and end with `Y`; either `X` or `Y`
  may be empty
- `.STR.`: searches for words that contain `STR`

For example, `search -d subt.` finds the definitions for words begining with
`subt`.

One further option is available for displaying the possible pronunciations of a
word, e.g.:

    $ ./search -p ginger

    - g|in|g|er     @↓.↑ / @↓→. / @↓.↑ / ←.↓
    - g|in|ge|r     @↓.↑ / @↓→. / @↓.← / ↓↑.
    - g|in|g|e|r    @↓.↑ / @↓→. / @↓.↑ / @_←. / ↓↑. 

The `-p` option shows all the ways the given word can be broken into phonemes,
and how to input those phonemes. An `@` means the sound is voiced, the first
arrow shows how to move the tongue, (or `_` for no input), and the second arrow
how to move the lips. A `.` before the lips instruction means the "speak" button
should be pressed before the lips, and a `.` after means the opposite.

For example:

- `←.↓` means tongue left, speak, lips down
- `@_←.` means voiced, no tongue input, lips left, speak

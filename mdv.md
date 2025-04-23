# MDV - Markdown command line viewer

## Install
- python3 and pip3

```bash
pipx install mdv
```

## Configure alias
```bash
mdv -t reddyred MDFILE
```

## Options
    MDFILE    : Path to markdown file
    -A        : Strip all ansi (no colors then)
    -C MODE   : Sourcecode highlighting mode
    -H        : Print html version
    -L        : Backwards compatible shortcut for '-u i'
    -M DIR    : Monitor directory for markdown file changes
    -T C_THEME: Theme for code highlight. If not set: Using THEME.
    -X Lexer  : Default lexer name (default: python). Set -x to use it always.
    -b TABL   : Set tab_length to sth. different than 4 [default: 4]
    -c COLS   : Fix columns to this (default: your terminal width)
    -f FROM   : Display FROM given substring of the file.
    -h        : Show help
    -i        : Show theme infos with output
    -l        : Light background (not yet supported)
    -m        : Monitor file for changes and redisplay FROM given substring
    -n NRS    : Header numbering (default: off. Say e.g. -3 or 1- or 1-5
    -t THEME  : Key within the color ansi_table.json. 'random' accepted.
    -u STYL   : Link Style (it=inline table=default, h=hide, i=inline)
    -x        : Do not try guess code lexer (guessing is a bit slow)

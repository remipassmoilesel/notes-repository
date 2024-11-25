# Delta git

Voir https://github.com/dandavison/delta

## Navigation

Utiliser `n` et `N` pour sauter de diff en diff.

## Exemple de config

```
$ cat ~/.gitconfig                                                                                                                                                                 [12:04:48]

[core]
    pager = delta

[interactive]
    diffFilter = delta --color-only

[delta]
    navigate = true    # use n and N to move between diff sections
    light = true # set to true if you're in a terminal w/ a light background color (e.g. the default macOS terminal)
    line-numbers = true

```

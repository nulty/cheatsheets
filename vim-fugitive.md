# Fugitive

Like vim in general, all concepts in fugitive are relative to the mode / buffer

There are 4 main buffer types relevant to fugitive:

1. fugitive (Gstatus)
2. fugitiveblame (Gblame)
3. git (git object, like a commit)
4. diff

# Gstatus

- `:G`  open status window
- `C-n` to iterate over files
- `C-p` to iterate backwards over files

- `-` to add or remove file from the index
    Can use this in Visual mode to select multiple files
- `Return` key opens the file in a new window

- `cc` create new git commit window
- `ca` commit --amend

# Gdiff

Index version on the left, Working Copy on the right.

### Stage all changes
 - `Gwrite` from working side
 - `Gread` from the index side

### Revert all changes
 - `Gwrite` from index side
 - `Gread` from the working side

### Undo
 - `u` in the index copy && `:diffupdate`

### Add hunk
  - `:diffget` to apply changes under the cursor
  - `:w` in the index file will `add` the changes to the index
  - Visual mode select lines and run diffget to add selection to index
  - `:diffupdate` to update the diff

# Gblame

- `filetype` : fugitiveblame

- `:Gblame` Open current file in blame
- `g?` open Gblame help mappings
- `gq` Quit blame back to working tree
- `p`  Open commit in preview window (bottom)
- `o`  Go directly to the change in the commit

    The `14241b1927` in the Gblame window is the object reference.
    Hitting `p` on this will open the horizontal split at the bottom of the vim instance


```
...

14241b1927  (Some Developer 2018-11-12 11:14:55 +0000)     end
14241b1927  (Some Developer 2018-11-12 11:14:55 +0000)   end
14241b1927  (Some Developer 2018-11-12 11:14:55 +0000) end
```


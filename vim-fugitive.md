# Gstatus

- `C-n` to iterate over files
- `C-p` to iterate backwards over files

- `-` to add or remove file from the index
    Can use this in Visual mode to select multiple files
- `Return` key opens the file in a new window

- `S-c` open git commit window

# Gdiff

Index version on the left, Working Copy on the right.

## Stage all changes
 - `Gwrite` from working side
 - `Gread` from the index side

## Revert all changes
 - `Gwrite` from index side
 - `Gread` from the working side

## Undo
 - `u` in the index copy && `:diffupdate`

## Add hunk
  - :diffget to apply changes under the cursor
  - :w in the index file will `add` the changes to the index
  - Visual mode select lines and run diffget to add selection to index
  - `:diffupdate` to update the diff



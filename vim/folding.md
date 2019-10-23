# Vim

### Folding

#### Setup

##### What is the fold method
```
:set fdm
foldmethod=manual
```

##### Set the fold method
`:set fdm=manual`

##### Editing the folds

- `zf[n]` Create a fold (use range or count lines)
- `zd` Delete this fold
- `zE` Delete ALL folds
- `zo` Open a fold under the cursor
- `zc` Close a fold under the cursor
- `zR` Open all folds


##### Indent can be useful in CSS files etc

`:set fdm=indent`

##### Naviagting folds

- `zj` Go to next fold
- `zk` Go to prev fold


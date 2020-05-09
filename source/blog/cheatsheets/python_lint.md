# Python lint
## yapf
.style.yapf
```
[style]
BASED_ON_STYLE = pep8
COLUMN_LIMIT = 120
SPLIT_BEFORE_NAMED_ASSIGNS = false
```
## flake8
.flake8
```
[flake8]
ignore =
    # Too many leading '#' for block comment (E266)
    E266
max-line-length=120
```

Nushell is a data analisys environment with an integrated shell, it works not on text but on objects, kind of like [Powershell](Powershell.md) but doesn't suck. 
e.g.
```nu
# find all directories
ls | where type == dir

# sort by newest ascending
ls | sort-by modified | reverse

# show all files ending with .json in all subdirectories which don't have node_modules in their name
ls **/*.json where name !~ node_modules

# show file as structured data
open Cargo.toml
```

- By default *output* will be in format `table -e` which means everything expanded but you can see just the top layer by piping it to `table`. 
- *Querying sqlite* databases with `open data.db | query db "select * from table"`, or inspect the schema with `open data.db | schema | table` 
- *Transpose* with `transpose`. 
- *Interact* with the data `explore`
- *http requests* `http get https://example.com/ | table`
- *parse* data `open somefile | get propertyName | parse "{day}/{month}/{year}"` for dates for example.
- *query web*, when used on a http get request can return only the files with some css properties e.g. `http get "https://example.com/" | query web -q "h2"` get all h2 headers from this url
-  get all *distinct authors* of commits of a git repo `git log | jc --git-log | from json | select author | uniq`


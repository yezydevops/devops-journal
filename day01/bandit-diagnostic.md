# Bandit Diagnostic (Levels 0-10)

| Level | Command I had to look up | What it does | Do I understand it now? |
|-------|--------------------------|--------------|-------------------------|
| 2     | cat ./- (dashed filenames) | ./ makes the name a path, so it isn’t read as an option or stdin | Yes |
| 5     | `find -size ! -executable` (! on syntax) | Filters on find, ! means NOT | Partly: unsure about the `c` suffix |
| 8     | `sort | uniq -u` (sort before pipe to uniq -u) | Sorts the lines first for uniq -q to effectively delete non-unique lines | Yes |
| 9     | `strings data.txt | grep -E ^=\+` (strings and -E in grep) | strings to filter string entries, -E to enable extended regex | Partly: still confused with regex |
| 10    | `base64 -d` | decodes base64 text back to the original | Partly | 

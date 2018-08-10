# Shell Snippets
- [Shell Snippets](#shell-snippets)
    - [Search and grep](#search-and-grep)
        - [Multiline grep](#multiline-grep)

## Search and grep
### Multiline grep
We can use `pcregrep` (or `pcre2grep.exe`) with options `-iM`

Example 1: to detect tag in XML-like file with duplicate attributes:
```shell
pcregrep -iMnHo --color "<[^>]+\s\b(\w+)=[^>]*\b\1=" file.xml
```
- `-i`: Ignore case
- `-M`: Multiline
- `-n`: Show line number
- `-H`: Force show filename
- `-o`: Show only part of the text that match the pattern
- `\b`: word boundary

Example 2: finding all duplicate attributes in tags from jsp files:

```shell
while read filename
do 
    pcre2grep.exe -iMl -o "<[^>]+\s\b(\w+)=[^>]*\b\1=" "${filename}"
done < <(find . -type f -name '*.jsp' -or -name '*.jspf)
```

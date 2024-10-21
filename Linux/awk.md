`awk` is a text manipulation binary that helps with making terminal output or file output easier to understand than it already is.

# Pre-defined and automatic variables and AWK
* **RS** - the record separator.
* **NR** - the current input record number
* **FS/OFS** - character that is used as the *field separator*. "White space" is the default for this.
* **NF** - Number of fields in the current record.

# Examples
## Remove a file header
`awk 'NR>1' file` 
`awk 'NR>1 { print }' file`
## Print lines in a range
`awk 'NR>1 && NR<4' file`
## Removing whitespace-only lines
`awk 'NF' file`
## Extracting fields
One of the most common use cases for AWK: extracting some columns of the data file.
`awk '{ print $1, $3 }' FS=, OFS=, file`

---
Related links:
[Linux Handbook | AWK](https://linuxhandbook.com/awk-command-tutorial/)

#linux #cmd
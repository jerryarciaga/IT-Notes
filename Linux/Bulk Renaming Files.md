I noticed that `ranger` 's bulk renaming function no longer works. As an alternative, you can use `rename` and a wildcard to perform a bulk rename using a `sed`-like syntax.

# Example
`rename -- 9780357368633_Kendall12e_ '' *.pdf`
Removed all instances of `9780357368633_Kendall12e_` on files that contain that string, simplifying the title.

I guess you can do something like `rename 's/ /_/g' *` to change all spaces into underscores.


---
Related links:
[Rename Multiple Files | Linux Handbook](https://linuxhandbook.com/rename-multiple-files/)
[This Question in Stack Overflow](https://stackoverflow.com/questions/5281956/renaming-a-set-of-files-in-linux)
[This other one from Unix Stack Exchange](https://unix.stackexchange.com/questions/1136/batch-renaming-files)

#linux #bash #file #sed #one-liner
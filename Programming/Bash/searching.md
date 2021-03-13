# Search
## Description
Search for files, folders and occurances.

## Find
```bash
find . -name "search_term" # Search for files matching *search_term*
find . -name "*.cpp" # Search for files matching widcard - extension
```

## grep
```bash
grep "search_term" "file" # Search for occurances of *search_term* in *file*
grep "search_term" * # Search all files in current folder (dir)
grep -w "search_term" * # Only display whole words
grep -i "search_term" * # Non-case sensitive 
grep -r "serch_term" * # Search sub-directories as well
grep -c "serch_term" * # Count number of matches
grep -x "serch_term" * # Only show those who exactly match
```

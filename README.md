# Useful Commands
This file provides a collection of useful commands that can be utilized while working in the command line interface.

## Grep Command
- Searches recursively (`-R`) in the current directory (`./`) for the string `search_string`.
- Excludes files named `tags` and directories named `output/`.
```
grep --exclude=tags --exclude-dir=output/ -R './' -e "search_string"
```

## Read First Line of All Files
- Uses `tail` to skip the first line (`-n +1`) of all files in the current directory with any extension (`*.*`).
```
tail -n +1 *.*
```

## Find Files in Current Directory
- Lists all files in the current directory (non-recursively) with the `.txt` extension using `find`.
```
find . -maxdepth 1 -type f -name "*.txt"
```

## Find Files and Tail
- Finds all files named `version.xml` in the current directory and its subdirectories, then outputs their content starting from the first line.
```
find . -iname "version.xml" -exec tail -n +1 {} +
```

## Find and Replace in Files
- Uses `find` to locate all `.txt` files in the current directory and its subdirectories, then replaces `search_string` with `replace_string` using `sed`.
```
find . -type f -name "*.txt" -exec sed -i 's/search_string/replace_string/g' {} +
sed -i -b -e 's/search_string/replace_string/g' `find . -name "*.txt"`
```

## Find and Replace in Files and create a backup file
- Searches for files matching the pattern `example_*` in the `/path` directory and replaces the string `search_string` with `replace_string` using `sed`. Creates a backup of the original file with the `.bak` extension.
```
find /path -type f -iname "*example_*" -exec sed -i.bak 's/search_string/replace_string/g' "{}" +;
```

## Install Python Library
- Installs the `python_lib` Python library using `pip`.
```
python -m pip install python_lib
```

## Install Library in Cygwin
- Installs the `package-name` package in Cygwin using `apt-cyg`.
```
apt-cyg install package-name
```
## Delete All Local Git Branches
- Deletes all local branches except the currently checked-out branch using `git branch`, `grep`, and `xargs`.
```
git branch -D `git branch | grep -v \* | xargs`
```


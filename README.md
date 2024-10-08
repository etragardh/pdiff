# pdiff
Utility for patch diffing


## Installation

```
gh repo clone etragardh/pdiff
chmod +x pdiff/pdiff
sudo ln -s ${PWD}/pdiff/pdiff /usr/local/bin
```

## Usage

**Normal operation**
```
pdiff ~/path/to/version-1.0 ~/path/to/version-1.1
```
This will be created in your working directory:
```
- ./diff/
| - original/		(modified files only, original state)
| - patch/		(modified files only, patched state)
| - repo/		(modified files only, git repo -> 2 states)
```

**Keep newly added files**
```
pdiff ~/path/to/version-1.0 ~/path/to/version-1.1 --keep
```
Output with kept files:
```
- ./diff/
| - original/		(modified files only, original state)
| - patch/		(modified and added files, patched state)
| - repo/		(modified and added files, git repo -> 2 states)
```

## Other

**Open VS Code in the git repo**
```
cd diff/repo
code .
```
VS Code can show you the file difference, side by side and color coded.<br />

The `diff/repo` directory contains a local git repository with both versions as commits. This is great if you want to compare the changes side by side.<br />

**Search the original files**

If you want to search for vulnerabilities it is convenient to search the modified files in their original state. ie if you are looking for reflected XSS you might want to run something like this in the `diff/original` directory.<br />

```
ag -l "POST|GET|COOKIE" | xargs ag -l "echo|print" | xargs ag "POST|GET|COOKIE|echo|print"
```

**Git commands in repo/**

You can also run ordinary git commands in the directory. Such as:
```
cd diff/repo
git log
git diff --name-only commit-id-1 commit-id-2
```

## Todo

+ Exclude CSS (option to keep)
+ Exclude JS (option to keep)
+ AI API (ask AI for dangerous practice and sample exploit)

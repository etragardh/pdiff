# pdiff
Utility for patch diffing

## Usage

**Installation**

```
gh repo clone etragardh/pdiff
chmod +x pdiff/pdiff
sudo ln -s ${PWD}/pdiff/pdiff /usr/local/bin
```

**Test it**
```
pdiff ~/path/to/version-1.0 ~/path/to/version-1.1
```

This will be created in your working directory:
```
diff/
 - mix/
 - patch/
```

The `diff/mix` directory contains a mix of modified and newly added files.<br />
However the modified files are stored in their original state (so you can search them for vulnerabilities).<br />
The newly added files are prefixed with `_a__` so you don't have to open them if not neccessary.
<br />
IE if you are looking for reflected XSS you might want to run something like this in the `diff/mix` directory.<br />
```
ag -l "POST|GET|COOKIE" | xargs ag -l "echo|print" | xargs ag "POST|GET|COOKIE|echo|print"
```

<br />
<br />
The `diff/patch` directory contains a local git repository with both versions as commits. This is great if you want to compare the changes side by side.<br />
ie if you have VS Code you can run `code .` and select `timeline` at the bottom left to get them side by side.<br /><br />

You can also run ordinary git commands in the directory. Such as:
```
git log
or
git diff --name-only commit-id-1 commit-id-2
```

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
pdiff path/to/version-1.0 path/to/version-1.1
```

`pdiff` will now create a new directory called `diff` in the working directory that contains only the modified and newly added files.<br />
<br />
However the `diff` directory will contain the orignal versions of the files, not the modified.<br />
<br >
This is great if you want to search for vulnerabilities.
<br />
IE if you are looking for reflected XSS you might want to run something like this in the `diff` directory.<br />
```
ag -l "POST|GET|COOKIE" | xargs ag -l "echo|print" | xargs ag "POST|GET|COOKIE|echo|print"
```

Newly added files are prefixed with `_a__`
<br />
FIXME: _a__ is also added to folder that holds new files

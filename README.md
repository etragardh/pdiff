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
IE if you are looking for reflected XSS you might want to run `ag 'POST|GET|COOKIES'` in the `diff` directory.<br />

Newly added files are prefixed with `_a__`

# findp
directory enumeration in parallel

Start FindFirstFile in multiple threads to speed up enumeration.
Lots of speedup when scanning shares via network.

+ search filename by substring
+ group and sum by extension

```
usage: findp.exe [OPTIONS] {directory}
Options:
  -f              ... print date, attributes, filesize, fullname
  -o              ... print owner when used with -f
  -s              ... sum dirs, files, filesize. don't print filenames
  -e [filename]   ... group extensions. 3 columns TAB separated: CountFiles | SumFilesize | Extension (UTF-8)
  -p              ... show progress
  -j              ... follow directory junctions
  -v              ... verbose/debug
  -h              ... show this help
  -t {f|d|b}      ... emit what  (files|directory|both) default: files
  -m {pattern}    ... substring to match within name. case insensitive. Not in full path.
  -d {depth}      ... how many directories to go down
  -x {threads}    ... threads to start for parallel enumerations. default: 32

prepend   \\?\   if you want to have long path support.
Samples:

          \\?\UNC\{server}\{share} for network paths
findp.exe \\?\c:\windows
```

# diff2html

This bash script formats diff(1) output to an HTML page on stdout.

It was created in 2009 by Kirk Roybal and is distributed under the GNU GPL license.

This git repository is based on diff2html version 0.07 as downloaded from https://sourceforge.net/projects/diff2html/


# Changelog since Kirk Roybal's version 0.07

- added --no-summary option to suppress summary output of differences with links
- fixed typo that prevented diff options from being forwarded to diff command

## Usage
```
Usage: diff2html [--help] [--copyleft] [--debug] [--no-style] [--no-header] [--only-changes] [--style-sheet file.css] [diff options] file1 file2

--help                 This message
--only-changes         Do not display lines that have no differences
--style-sheet file.css Use an alternative style sheet URL
--no-style             Suppress the inclusion of a style sheet
--no-header            Suppress the HTML,HEAD and BODY tags
--no-summary           Suppress the summary section with links to differences
--debug                Way too much output for you
--copyleft             Show the GNU v3 license
--version              Show the version number and exit
diff options           All other parameters are passed to diff

## Examples

Basic example:

```diff2html file1.txt file2.txt > differences.html```

Treat all files as text, even if they contain binary data, and compare them line-by-line:

```diff2html -a file1 file2 > differences.html```

Use a custom style sheet:

```diff2html --style-sheet diff_style.css -a file1 file2 > differences.html```

Pipe stdout of diff to stdin of diff2html (slightly faster):

```diff file1 file2 | diff2html [options] file1 file2```

## The default, hard-coded style sheet

```
<style>
TABLE { border-collapse: collapse; border-spacing: 0px; }
TD.linenum { color: #909090;
   text-align: right;
   vertical-align: top;
   font-weight: bold;
   border-right: 1px solid black;
   border-left: 1px solid black; }
TD.added { background-color: #DDDDFF; }
TD.modified { background-color: #BBFFBB; }
TD.removed { background-color: #FFCCCC; }
TD.normal { background-color: #FFFFE1; }
</style>
```

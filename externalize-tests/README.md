# TikZ Externalize in standalone document class

## Tests

| latex dist.  | compiler | externalize enabled | output dir | success |
| :----------- | :------: | :------------------ | :--------: | :------ |
| TeXLive 2016 | pdflatex | no                  | -          | yes     |
| TeXLive 2016 | pdflatex | no                  | build      | yes     |
| TeXLive 2016 | pdflatex | yes                 | -          | yes     |
| TeXLive 2016 | pdflatex | yes                 | build      | yes     |
| TeXLive 2016 | lualatex | no                  | -          | yes     |
| TeXLive 2016 | lualatex | no                  | build      | yes     |
| TeXLive 2016 | lualatex | yes                 | -          | yes     |
| TeXLive 2016 | lualatex | yes                 | build      | yes     |


Commands used for TeXLive and PDFLaTeX:

 * pdflatex tikz-external-minimal
 * pdflatex -output-directory=build tikz-external-minimal
 * pdflatex -shell-escape tikz-external-minimal
 * pdflatex -shell-escape -output-directory=build tikz-external-minimal

Commands used for TeXLive and LuaLaTeX:

 * lualatex tikz-external-minimal
 * lualatex --output-directory=build tikz-external-minimal
 * lualatex --shell-escape tikz-external-minimal
 * lualatex --shell-escape --output-directory=build tikz-external-minimal


## Problems

### System calls (shell-escape command-line option)

When activating the externalize functionality with \externalize command,
the TeXLive 2016 pdflatex compiler cannot externalize the tikz pictures
and an error like this is thrown:

  ===== 'mode=convert with system call': Invoking 'pdflatex -halt-on-error -interaction=batchmode -jobname "external/tikz-external-minimal-figure0" "\def\tikzexternalrealjob{tikz-external-minimal}\input{tikz-external-minimal}"' ========
  ! Package tikz Error: Sorry, the system call 'pdflatex -halt-on-error -interaction=batchmode -jobname "external/tikz-external-minimal-figure0" "\def\tikzexternalrealjob{tikz-external-minimal}\input{tikz-external-minimal}"' did NOT result in a usable output file 'external/tikz-external-minimal-figure0' (expected one of .pdf:.jpg:.jpeg:.png:). Please verify that you have enabled system calls. For pdflatex, this is 'pdflatex -shell-escape'. Sometimes it is also named 'write 18' or something like that. Or maybe the command simply failed? Error messages can be found in 'external/tikz-external-minimal-figure0.log'. If you continue now, I'll try to typeset the picture.
  See the tikz package documentation for explanation.
  Type  H <return>  for immediate help.
  ...                                              
  l.38 \end{tikzpicture}

Note that the LuaLaTeX compiler requires the shellesc package to be able to use system calls.


### Can't write on file (prefix feature)

When enabling the prefix feature in combination with a separate output directory,
the up-to-date check cannot write the md5 file (or something similar)
and an error like this is thrown:

  ! I can't write on file `external/tikz-external-minimal-figure0.md5'.
  <to be read again> 
  \relax 
  l.34 \end{tikzpicture}
  (Press Enter to retry, or Control-D to exit; default file extension is `.tex')

The reason is that the md5 file goes to the <output>/<prefix> directory
and latex cannot create that directory for you.
This, when this directory does not exists, the latex compilation process fails.


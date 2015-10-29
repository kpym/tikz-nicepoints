# tikz-nicepoints
This is a TikZ library named **`nicepoints`** that makes it easy to draw points.

This code is similar to this [TeX.SX answer](http://tex.stackexchange.com/a/220760)  

## How to use it
* Put `tikzlibrarynicepoints.code.tex` file in a folder accessible by latex. 
  For example in the same folder as your main file.
* Load the library with 
```latex
\usetikzlibrary{nicepoints}
```

## Basic usage examples
![example basic usage](https://raw.githubusercontent.com/kpym/tikz-nicepoints/master/examples/nicepoints-example-basic.png)

* `[point]` draws a point whose size is dependant of the current line width, whose "border" color is the salme as the text color.
   - custom size :
        * `[thick,point]` or `[point=thick]` set the point to the size corresponding to "thick" line;
        * `[point size=4pt,point]` or `[point={point size=4pt}]` set the point to the size corresponding to 4pt line.
   - custom color :
        * `[red,point]` or `[point=red]` draw the point in red
        * `[point fill=yellow, point]` or `[point={point fill=yellow}]` fill the point in yellow (the default is white)
* `[point="A"]` makes 3 things :
  * (1) same as `[point]`
  * (2) name the point coordinates as `(A)`
  * (3) put the label `$A$` next to the point
* `[point="A"*]` or `[point="A"']` makes the same (1) and (2), but without (3). This is equivalent to [point]coordinate(A).
* `[point="A"blue]` or `[point="A"{blue,below}]` set the style of the lable `$A$` to `[blue]` or `[blue,below]`.
* `[point={label=$B$}]` is equivalent making 1) and 3), without 2).
* `node[point,above]{$B$}` is the same as `[point] node[above]{$B$}`
* `\point["A"red] at (1,1);` is the same as `\path (1,1) [point="A"red]`;


## More examples

* Example 1 
```latex
\documentclass[border=7pt]{standalone}
\usepackage{tikz}
\usetikzlibrary{nicepoints}

\begin{document}
  \begin{tikzpicture}[thick]
    \draw[yshift=0mm] (0,0) -- (1,0) [point] node[below,blue,font=\tt]{[point]} -- (2,0);
    \draw[yshift=-7mm] (0,0) -- (1,0) [ultra thick,point=red] node[below,blue,font=\tt]{[ultra thick,point=red]} -- (2,0);
    \draw[yshift=-14mm] (0,0) -- (1,0) [point={ultra thick,point fill=yellow}] node[below,blue,font=\tt]{[point=\{ultra thick,point fill=yellow\}]} -- (2,0);
    \draw[yshift=-24mm] (-1.5,0) [point="A"left] node[below,blue,font=\tt]{[point="A"left]} -- (1,0) [point="B"] node[below,blue,font=\tt]{[point="B"]} -- (3.5,0) [point="C"*] node[below,blue,font=\tt]{[point="C"*]};
    \point["P"red] at (1,-35mm) node[below,blue,font=\tt]{\textbackslash point["P"red] at (1,0);};
  \end{tikzpicture}
\end{document}
```
![example 1](https://raw.githubusercontent.com/kpym/tikz-nicepoints/master/examples/nicepoints-example1.png)

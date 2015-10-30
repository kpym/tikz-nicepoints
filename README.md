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

* `[point]` draws a point whose size is dependent of the current line width, whose "border" color is the salme as the text color.
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
* `[point="A"blue]` or `[point="A"{blue,below}]` set the style of the label `$A$` to `[blue]` or `[blue,below]`.
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
  \begin{tikzpicture}[scale=2]
    \draw[fill=yellow!30,very thick]
      (0,0) [point="A"] -- (1,0) {[blue,point="B"right]}
      -- node[red,point="C"*,left]{$\mathcal{C}$} (1,1) [point="D"{above,red}]
      -- (0,1) [point={red,"E"}];
    \draw[thick,purple] (E) -- (B) to[bend right] (D) edge[bend right] (C) [point=near start];
  \end{tikzpicture}
\end{document}
```
![example 1](https://raw.githubusercontent.com/kpym/tikz-nicepoints/master/examples/nicepoints-example1.png)

## Layers
This library declare one additional layer called `points` , and draws all points in this layer. 
This layer sits above the main layer, so even if a point is drawn before some line, it remains visible.

If you want to add your own layers, you have to add to this layer too, for example like this 

```latex
\pgfsetlayers{background,main,foreground,points}
```

## Reset font
If the current font has a dot that is not well centered, you can reset the font used by `[point]` to be Latin Modern by adding the style `[lmpoint]`.

## License

This file may be distributed and/or modified

  1. under the LaTeX Project Public License and/or
  2. under the GNU Public License.

Both licenses are available in the LICENSES folder.

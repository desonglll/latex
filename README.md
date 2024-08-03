
### Wiki

[LaTeX/Document Structure](https://en.wikibooks.org/wiki/LaTeX/Document_Structure#Document_classes)

### MacTex

[MacTex Official](http://tug.org/mactex/)

### Using in VSCode

Install `LaTeX Workshop` in VSCode.

### Configuration

[MACOS下用Vscode配置LaTex(2022_07_18)亲测有效](https://blog.csdn.net/m0_48235336/article/details/125842693)

这段代码包括了

①XeLaTeX的配置

②两次编译 XeLaTeX，防止有些时候目录不显示（血泪）

③删除部分不需要的Tex编译时产生的多余文件

④以上都是我一个个自己搜出来加上去的

```json
{
    "js/ts.implicitProjectConfig.checkJs": true,
    "latex-workshop.latex.tools": [
        {
          "name": "xelatex",
          "command": "xelatex",
          "args": [
            "-synctex=1",
            "-interaction=nonstopmode",
            "-file-line-error",
            "%DOC%"
          ]
        },
        {
          "name": "pdflatex",
          "command": "pdflatex",
          "args": [
            "-synctex=1",
            "-interaction=nonstopmode",
            "-file-line-error",
            "%DOC%"
          ]
        },
        {
            "name": "latexmk",
            "command": "latexmk",
            // "args": [
            //     "-synctex=1",
            //     "-interaction=nonstopmode",
            //     "-file-line-error",
            //     "-pdf",
            //     "-outdir=%OUTDIR%",
            //     "%DOC%"
            // ],
            "args": [
                "-xelatex",
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOC%"
            ],
            "env": {}
        },
        /*
        {
          "name": "latexmk",
          "command": "latexmk",
          "args": [
            "-synctex=1",
            "-interaction=nonstopmode",
            "-file-line-error",
            "-pdf",
            "%DOC%"
          ]
        },
        */
        {
          "name": "bibtex",
          "command": "bibtex",
          "args": [
            "%DOCFILE%"
          ]
        }
      ],
      "latex-workshop.latex.recipes": [
        {
          "name": "XeLaTeX",
          "tools": [
            "xelatex",
            "xelatex"
          ]
        },
        {
          "name": "PDFLaTeX",
          "tools": [
            "pdflatex"
          ]
        },
        {
          "name": "latexmk",
          "tools": [
            "latexmk"
          ]
        },
        {
          "name": "BibTeX",
          "tools": [
            "bibtex"
          ]
        },
        {
          "name": "xelatex -> bibtex -> xelatex*2",
          "tools": [
            "xelatex",
            "bibtex",
            "xelatex",
            "xelatex"
          ]
        },
        {
          "name": "pdflatex -> bibtex -> pdflatex*2",
          "tools": [
            "pdflatex",
            "bibtex",
            "pdflatex",
            "pdflatex"
          ]
        },
    ],
    "latex-workshop.latex.autoClean.run": "onBuilt", //注意结尾是 t 不是 d
    "latex-workshop.latex.clean.fileTypes": [
      "*.aux",
      "*.bbl",
      "*.blg",
      "*.idx",
      "*.ind",
      "*.lof",
      "*.lot",
      "*.out",
      "*.toc",
      "*.acn",
      "*.acr",
      "*.alg",
      "*.glg",
      "*.glo",
      "*.gls",
      "*.ist",
      "*.fls",
      "*.log",
      "*.fdb_latexmk",
    ],
}
```
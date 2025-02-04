# pkuthss: LaTeX template for dissertations in SECE of PKU

基于北大硕士论文模板: [Thesharing/pkuthss](https://github.com/Thesharing/pkuthss)。使用指南见下文原README文件的内容。

结合信工学院的论文要求，本项目改动了以下内容：

1. 引入图和表格的双语标题。使用示例：`\bicaption{填入中文标题}{fill in English caption}`，如仅需中文标题，可以使用：`\caption{填入中文标题}`。

2. 引入章节缩写表（chap/terms.tex），引入章节科研成果（chap/achieve.tex）。

3. 参考文献格式的人名采用`gbnamefmt=quanpin`。

4. 按照北大论文要求，摘要及之后的章节去除了空白页。见thesis.tex中`\let\cleardoublepage\relax`。因此chap/abs.tex中的中文和英文摘要之间多插入一个`\clearpage`。同时后续的科研成果和致谢部分手动添加了空白页`\clearpage{\thispagestyle{empty}\cleardoublepage}`

5. 引入自动生成的《图目录》和《表目录》，以及需要自行填写的《缩写表》，对应thesis.tex中`\listoffigures`和`\listoftables`，以及chap/terms.tex。

6. thesis.tex中加入`\special{dvipdfmx:config z 0}`，用于取消PDF压缩，加快编译速度。提交终板时可以删除此命令。

7. 封面题目的字体改为一号大小，表格内容的字体改为11pt大小。

注意：如提示FangSong字体未找到，可以将pkuthss.cls文件中的`\thss@int@boolopt{pkufont}{true}`的`true`改为`false`。其他部分请参考下文的原README内容。

关于查重等未尽事宜，可以查看本项目的相关issue，或发起新issue。如需要撰写信工学院的开题报告，可使用同为LaTeX版的开题报告[asuith/pkuszdp](https://github.com/asuith/pkuszdp)。

以下是[Thesharing/pkuthss](https://github.com/Thesharing/pkuthss)的原README内容。

---
# pkuthss: LaTeX template for dissertations in Peking University

Source: [CasperVector/pkuthss](https://github.com/CasperVector/pkuthss)

## Changes

相比于原模板有以下改动：

* 修改了copy.tex的行距
* 修改了origin.tex的勾选框和行距
* 将make.bat和Makefile中默认编译方式改为xelatex
* 将Hyperlink的颜色修改为黑色
* 为目录添加了点线
* 增加了`nopkumathfont`选项，仅将数学公式字体恢复为默认字体
* 将页眉修改为“硕士学位论文”（如果需要修改成其他的，参考pkuthss.cls的313行）
* 修改了封面标题的字体大小
* 为中英文关键字添加了缩进
* 将Bibtex模板由CapserVector改为biblatex-gb7714-2015

## Environment

参考 [VSCode + LaTeX](https://zhuanlan.zhihu.com/p/108095566)

For TeX compiler:

1. Install TeXLive 2020 [here](https://www.tug.org/texlive/).

For editor:

1. Install Visual Studio Code [here](https://code.visualstudio.com/).
2. Install LaTeX Workshop [here](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop).
3. Install LaTeX Untilities [here](https://marketplace.visualstudio.com/items?itemName=tecosaur.latex-utilities).

For bibliography:

1. Install Zotero [here](https://www.zotero.org/download/).
2. Install ZotFile [here](http://zotfile.com/).
3. Install Better BibTex for Zotero [here](https://github.com/retorquere/zotero-better-bibtex).

Recommend:

Use [MathPix Snip](https://mathpix.com/) to OCR the equations.

## Compile

For Windows, run `make.bat doc`.

For Linux/macOS, run `make doc`.

## Reference

1. [TeX Live + pkuthss 安装使用傻瓜指南 v0.1.6](https://bbs.pku.edu.cn/v2/post-read-single.php?bid=346&type=0&postid=18114839)
2. [CasperVector/pkuthss](https://github.com/CasperVector/pkuthss)
3. [hushidong/biblatex-gb7714-2015](https://github.com/hushidong/biblatex-gb7714-2015)
3. [VSCode + LaTeX](https://zhuanlan.zhihu.com/p/108095566)
4. [使用VSCode编写LaTeX](https://zhuanlan.zhihu.com/p/38178015)
5. [VS Code 与 LaTeX 真乃天作之合](https://www.jianshu.com/p/57f8d1e026f5)

## Appendix

### LaTeX Workshop Setting

```json
{
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
            "name": "biber",
            "command": "biber",
            "args": [
                "-l",
                "zh__pinyin",
                "--output-safechars",
                "%DOCFILE%"
            ],
        }
    ],
    "latex-workshop.latex.recipes": [
        {
            "name": "Compile thesis",
            "tools": [
                "xelatex",
                "biber",
                "xelatex",
                "xelatex"
            ]
        }
    ]
}
```


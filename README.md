# LaTeX-Template

これは、LaTeXでノートや資料を作るためのテンプレートです。

[サンプルPDF](example_notebook/build/main.pdf)

## 準備

このテンプレートを使うには

* 完全な TeX Live 環境

が必要です。
Windowsについては、[WSL](https://learn.microsoft.com/ja-jp/windows/wsl/install)を使ってUbuntuをインストールするのが便利です。
WSLでの動作確認はできています。

Ubuntu ならば、以下のコマンドでインストールできます。

```bash
sudo apt install texlive-full
```

また、~/.latexmkrcに以下の内容を書いておくと、`latexmk main`というコマンドでコンパイルできます。

```perl
# LuaLaTex
$lualatex = 'lualatex --synctex=1 --file-line-error --shell-escape --halt-on-error %O %S';
$out_dir = 'build';
$pdf_mode = 4;
$max_repeat = 5;
```

## 使い方

GitHubで「Use this template」をクリックして、リポジトリを作成するのが便利です。

使用する際にはドキュメントのプリアンブル部分に以下のように書いてください。

```tex
\documentclass[お好みのオプション]{ltjsreport}

\usepackage{import}
\import{preamble.texがあるディレクトリまでのパス}{preamble}

\begin{document}
... 本文 ...
\end{document}
```

## 設定の編集方法

このテンプレートは、`ltjsreport`向けに設定されています。
設定は`preamble/`内のファイルに分けて書かれており、それを`preamble.tex`で参照している形になっています。

`preamble/`内のファイルを編集することで、設定を変更することができます。
それぞれのファイルの役割は以下の通りです。

* `page.tex`: ページの余白やヘッダー・フッターの設定
* `text.tex`: フォントや文字サイズ、文章の設定
* `math.tex`: 数式の設定
* `figure.tex`: 図表の設定
* `environment.tex`: 環境の設定

利用目的に合わせて、適宜編集してください。
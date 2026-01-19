# LaTeX 執筆用テンプレート (卒業論文・レジュメ対応)

このリポジトリは、LaTeXを初めて使う人でもスムーズに卒業論文やレジュメ（研究概要）の執筆を開始できるように構成されたテンプレートです。

## 1. 環境構築 (Windows + VS Code 推奨)

以下の手順でLaTeXの執筆環境を整えてください。

### Step 1: TeX Live のインストール
LaTeXの本体です。容量が大きいため（数GB）、安定したネット環境で実行してください。
- [TeX Live インストールガイド](https://texwiki.texjp.org/?TeX%20Live/Windows) を参照してインストールします。
- 詳細なセットアップ手順については、こちらの記事も参考にしてください：[Windows 11 に TeX Live をインストールして VS Code で執筆環境を作る](https://zenn.dev/hash_yuki/articles/31855fbdb5fdf7)

### Step 2: VS Code と拡張機能の導入
エディタとして **Visual Studio Code (VS Code)** を使用します。
1. VS Codeをインストールします。
2. 拡張機能マーケットプレイスで **「LaTeX Workshop」** を検索してインストールします。

### Step 3: このリポジトリを開く
このフォルダ全体を VS Code で開いてください。`.vscode/settings.json` に最適な設定があらかじめ記述されているため、特別な設定なしで美しくビルド・整形ができます。

---

## 2. リポジトリの利用方法 (Git)

このテンプレートを初めて自分のPCに持ってくる場合や、最新の状態に更新する場合は以下のコマンドを使用します。

### 初めて利用する場合 (Clone)
任意の作業フォルダで以下のコマンドを実行します。
```bash
git clone https://github.com/snjk17/latex-setting.git
```

### 最新の状態に更新する場合 (Pull)
すでにリポジトリをダウンロード済みで、他の人が更新した内容を取り込みたい場合は、フォルダ内で以下のコマンドを実行します。
```bash
git pull origin main
```

---

## 3. ファイル構成

主なファイルと役割は以下の通りです。

- `main.tex`: **卒業論文用**のメインファイル。
- `resume.tex`: **レジュメ（研究概要）用**のメインファイル。
- `subfigure.sty`: **複数の図を並べて配置**するためのパッケージ。
- `IPS-abstract.sty`: レジュメ用のスタイルファイル（レイアウト設定）。
- `osaka_logo.pdf`: タイトルページに使用するロゴ画像。
- `out/`: ビルド（コンパイル）後のPDFや中間ファイルが生成される場所。
- `.vscode/`: VS Codeの設定ファイル（保存時の自動整形やビルド設定）。

---

## 3. 基本的な使い方

### 編集する
`main.tex` または `resume.tex` を開き、内容を書き換えてください。
- 箇条書きや数式、図の挿入方法は、ファイル内のコメントを参考にしてください。

### ビルドする (PDFを作る)
1. ビルドしたい `.tex` ファイル（`main.tex` または `resume.tex`）をアクティブにします。
2. **`Ctrl + Alt + B`** キーを押すと、ビルドが始まります。
3. `out/` フォルダの中にPDFが生成されます。
4. VS Code の右上の「View PDF」アイコン（再生ボタンのようなマーク）を押すと、VS Code内でPDFを確認できます。

### 自動整形 (Format)
ファイルを保存すると、インデント（字下げ）などが自動で綺麗に揃えられます。

---

## 4. 執筆のヒント

### 参考文献の管理
1. `ref.bib` (まだない場合は作成) に BibTeX 形式で文献情報を書きます。
2. 本文中で `\cite{キー}` を使って引用します。

### 図の挿入 (1つだけ配置する場合)
画像ファイルはプロジェクト内に保存し、以下のコードで挿入します。
```latex
\begin{figure}[htbp]
  \centering
  \includegraphics[width=0.8\linewidth]{画像ファイル名}
  \caption{説明文}
  \label{fig:my_label}
\end{figure}
```

### 図の挿入 (複数の図を並べて配置する場合)
`subfigure.sty` を使用して、(a), (b) のように図を並べることができます。
```latex
\begin{figure}[htbp]
  \centering
  \subfigure[左側の図の説明]{
    \includegraphics[width=0.45\linewidth]{photo1.pdf}
    \label{fig:left}
  }
  \hfill
  \subfigure[右側の図の説明]{
    \includegraphics[width=0.45\linewidth]{photo2.pdf}
    \label{fig:right}
  }
  \caption{全体の大きなタイトル}
  \label{fig:total}
\end{figure}
```

### 数式の書き方
インライン数式は `$E=mc^2$`、独立した数式は `equation` 環境を使います。
```latex
\begin{equation}
    x + y = z
\end{equation}
```

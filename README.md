
# 博論テンプレート

私が同志社大学大学院の博論を書くために作ったものです．
[このレポジトリ](https://github.com/Veerachart/Thesis-template)をベースにしています．

## Publicationsについて

Publicationsの章を作成するのにかなり苦戦したのでメモ．やりたいこととしてはPublicationsという章のなかに複数の節（e.g., Journal, International Conference）を持たせたい．

### How To

> [!CAUTION]
> 使用する`.bst`ファイルを変更した場合，1.からやり直す必要があるので注意．

> [!TIPS]
> `.bbl`ファイルからのコピペをするのは書式を合わせるためだけなので，自信があるのであれば`\bibitem`直書きでも良い．推奨はしない．

1. `main.tex`内で`multibib`関連の設定をしてPublicationsの章を生成．

    - 以前に書いたPublicationの章が存在する場合コメントアウトが無難．

    - この段階ではSectionに分けられていない．

2. この時に生成されるPublicationsの章に関する`.bbl`を保存．

3. `thesis.sty`で定義されている`thepublications`環境内に`.bbl`からコピペ．

    - 場所はどこでも．`main.tex`内に直接でもいいし，[ここにあるように](./chapters/publications.tex)ファイルに書き込んで`main.tex`で`\input{}`しても良い．

4. `main.tex`内の`multibib`関連をコメントアウト．

5. コンパイル．

### Publicationsの章の例

```tex
\chapter*{Publications}
\addcontentsline{toc}{chapter}{Publications} % tocに追加

% one `thepublications` environment creates a section not a chapter.
\begin{thepublications}{Journal Papers}{9}
  \bibitem{key1}
  \underline{First Last} and First Last, ``Title,'' \emph{Journal}, vol.~xx, no.~xx, 20xx. [Online]. Available: \url{https://doi.org/xx.xxxx/xxxxxxxxxxxxxx}
\end{thepublications}

\begin{thepublications}{International Conference}{9}
  \bibitem{key2}
  \underline{First Last} and First Last, ``Title,'' in \emph{Conference}, 20xx, pp. xxx--xxx. [Online]. Available: \url{https://doi.org/xx.xxxx/xxxxxxxxxxxxxx}
\end{thepublications}

\begin{thepublications}{Domestic Conference}{9}
  \bibitem{key3}
  \underline{姓名}，姓名，``タイトル''，学会，20xx，pp. xxx--xxx．
\end{thepublications}
```

### How

一応備忘録を残す．

#### `thepublications`環境

jsreportクラスの`thebibliography`環境を書き換えて，章ではなくSectionを作るようにしたもの．ついでにセクションの名前を指定できるようにした．

#### Why not

- `biblatex`

  日英混合の場合`biblatex`のスタイル指定がめんどくさそうなので諦め．英論文しかない場合は`biblatex`が楽なのでそちらを推奨．

- `multibib`

  Sectionに分割する方法を見つけられなかった．

## Author

[Tomoya Sawada](https://github.com/STomoya)

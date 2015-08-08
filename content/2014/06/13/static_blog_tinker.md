Title: A static blog generator - Tinkerer
Date: 2014-06-13 00:00
Category: Blog
Tags:
Slug: static_blog_tinkerer
Authors: shinbo91

常見的 Static Blog Generator 有很多，像 [Pelican][], [Octopress][], 或是 [Jekyll][] 等等。
而 [Tinkerer][] 是 [Sphinx][] 下的一個 extension，專門用來將 ReST 文件轉換成 Blog 的文章。
所以若是熟悉 [Sphinx][] 及 ReST 語法的話，那麼用 [Tinkerer][] 來寫 Blog 應該會是一件很容易的事。

在已經安裝了 [Sphinx][] 的環境中，要使用 Tinkerer 的話，可透過下列的方式來安裝

```
$ easy_install -U Tinkerer

or

$ pip install Tinkerer
```

安裝完成後，便可透過下列的指令，來得知可使用的參數

```
$ tinker --help
```

常用的參數如下

```
$ tinker -s                     # 在此目錄下建立一個 Tinkerer 的 Blog
                                # 所有需要用到的檔案
$ tinker -d 'foo bar'           # 建立一個 drafts/foobar.rst 的 draft 文件
                                # 其文章標題為 foo bar
$ tinker -p drafts/foo_bar.rst  # 將 draft/foo_bar.rst 文件
                                # 移到該文章建立日期所對應的目錄中
                                # 以產生一個 post 文件
$ tinker -b                     # 將所有 post 文件轉換成 HTML
                                # 並放置於 blog/html/ 下對應的目錄之中
```

在執行完 **tinker -s** 這個指令之後，會在所在目錄下產生所有必要的檔案，以及最重要的 conf.py。這個檔案，主要是用來變更該 Blog 的相關資訊及設定之用。

剩下的工作，就是撰寫 Rest 文件來建立文章，最後再透過 [Tinkerer][] 將 ReST 文件轉換成 Static Blog。
相關資訊都可以在 [Tinkerer][] 網站的 [Document](http://tinkerer.me/pages/documentation.html) 中找到

# Theme

目前 [Tinkerer][] 中所能夠使用的 Theme 並不多，基本的幾個內建 Theme 如下：

- flat
- modern5
- minimal5
- responsive
- dark

在 conf.py 中，只要變更 **html_theme** 這個變數的值，就可以指定該 Blog 要使用的 Theme。

```
# Pick another Tinkerer theme or use your own
html_theme = "modern5"
```

另外，在網路上，也有一些熱心人仕所做的 Theme。
例如:

- [tinkerturquoise](https://github.com/naoiwata/sphinxjp.themes.tinkerturquoise)
- [tinkerpress](https://github.com/shkumagai/sphinxjp.themes.tinkerpress)
- [tinkeralizarin](https://github.com/naoiwata/sphinxjp.themes.tinkeralizarin)
- [tinkerbelizehole](https://github.com/naoiwata/sphinxjp.themes.tinkerbelizehole)
- [Tinkerbelizeholesidebar](https://github.com/naoiwata/sphinxjp.themes.tinkerbelizeholesidebar)

透過該網址中的說明，再加以設定後，就可以套用該 Theme。像我目前所選的這個，就是 **tinkerturquoise** 這個 Theme。

# GitHub Pages

在透過 [Tinkerer][] 產生 Static Blog 之後，必須將這些 HTML 相關檔案放置到網頁空間上，這樣其他人才可以在網路上瀏覽該 Blog。
而在 [GitHub][] 上也有提供 webpage hosting 的服務，主要可分成兩種形式:

1. Project page
2. User page

Project page 主要在 [GitHub][] 上透過 [GitHub Pages][]，可以讓 Repository 擁有各自的網頁，而該網頁的連結 URL 會是 **http://username.github.io/repo-name/**。
詳細資訊可參考 [Creating Project Pages manually](https://help.github.com/articles/creating-project-pages-manually)。

User Page 不同於 Project Page，主要是來產生使用者的網頁。
在使用 User Page 來建立網站時，必須建立一個叫 username.github.io 的 Repository，並將網頁 commit 到該 Repository 的 master branch 中。
接著 push 到 [GitHub][] 後，便會產生一個可供使用者瀏覽的網站。一般來說，User page 連結的 URL 為 **http://username.github.io/**。
有關 User page 的詳細資訊，可參考 [User & Organization Pages](https://help.github.com/articles/user-organization-and-project-pages#user--organization-pages)

[Pelican]: http://getpelican.com/
[Octopress]: http://octopress.org/
[Jekyll]: http://jekyllrb.com
[Tinkerer]: http://tinkerer.me
[Sphinx]: http://sphinx-doc.org
[GitHub]: https://github.com/
[GitHub Pages]: https://pages.github.com/

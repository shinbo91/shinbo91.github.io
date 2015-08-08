Title: Pelican Quickstart
Date: 2015-08-06 20:20
Category: Blog
Tags: pelican, mac
Slug: pelican_quickstart
Authors: shinbo91

[Pelican][] 跟 [Octopress][] 一樣是一個 Static Blog Generator, 除了支援 ReST 語法外, 同時也支援 Markdown 語法。
由於 Markdown 簡單、易寫的特性, 使用 Markdown 語法來撰寫文件的情況可以說是越來越常見了。

[Pelican][] 是使用 [Python][] 撰寫完成的 Blog 系統, 所以在 Windows, Linux, 甚至是 Mac 上都可以執行。

首先, [Pelican][] 官方文件上建議使用 Virtualenv 來執行，所以先安裝 Virtualenv 並建立一個虛擬環境

```
$ pip install virtualenv
$ cd /path/to/env/
$ virtualenv blogenv
$ source blogenv/bin/activate
```

接著, 使用 pip 安裝下列 package

```
$ pip install pelican
$ pip install markdown
```

# Setup

接下來，在 shell 中先將所在目錄切換到要放置 blog 資料的目錄，然後執行 pelican-quickstart 進行設定

```
$ mkdir /path/to/myblog
$ cd /path/to/myblog
$ pelican-quickstart

Welcome to pelican-quickstart v3.6.2.

This script will help you create a new Pelican-based website.

Please answer the following questions so this script can generate the files
needed by Pelican.

> Where do you want to create your new web site? [.] 
> What will be the title of this web site? shinbo91 blog
> Who will be the author of this web site? shinbo91
> What will be the default language of this web site? [en]
> Do you want to specify a URL prefix? e.g., http://example.com   (Y/n) 
> What is your URL prefix? (see above example; no trailing slash) http://shinbo91.github.io
> Do you want to enable article pagination? (Y/n) 
> How many articles per page do you want? [10]
> What is your time zone? [Europe/Paris] Asia/Taipei
> Do you want to generate a Fabfile/Makefile to automate generation and publishing? (Y/n) 
> Do you want an auto-reload & simpleHTTP script to assist with theme and site development? (Y/n)
> Do you want to upload your website using FTP? (y/N)
> Do you want to upload your website using SSH? (y/N) 
> Do you want to upload your website using Dropbox? (y/N) 
> Do you want to upload your website using S3? (y/N) 
> Do you want to upload your website using Rackspace Cloud Files? (y/N)
> Do you want to upload your website using GitHub Pages? (y/N) Y
> Is this your personal page (username.github.io)? (y/N) N
```

上面的步驟執行完之後, [Pelican][] 會在 myblog/ 下產生所有必需的檔案，而 pelican-quickstart 的設定值則填入 pelicanconf.py 中。

下面是 pelicanconf.py 中常用的設定, 可隨時更改 pelicanconf.py 中的設定值, 以進行 [Pelican][] 的調整。

```
AUTHOR = u'shinbo91'                  # 作者名稱
SITENAME = u"shinbo91's blog"         # Blog 標題
SITEURL = 'http://shinbo91.github.io' # Blog 的 URL
TIMEZONE = "Asia/Taipei"              # 時區
DEFAULT_LANG = u'zh_TW'               # 預設使用語言
THEME = "/path/to/theme"              # 佈景主題
```

# Theme

Theme 預設是採用跟 [Pelican][] 相同的風格, 若是要使用其他的 Theme, 可參考使用 [Pelican Themes][] 中的 Theme。

執行下面的指令, 取得 [Pelican Themes][] 的檔案
```
$ git clone --recursive https://github.com/getpelican/pelican-themes /path/to/pelican-themes
```

接下來, 在 pelicanconf.py 中指令要使用的 Theme, 並重新發怖即可。

```
THEME = "/path/to/pelican-themes/tuxlite_tbs"
```

# Writing content

在 [Pelican][] 上要撰寫 Blog 的文章, 需在 myblog/content/ 目錄建立 Markdown 格式的檔案

```
Title: Hello World
Date: 2015-08-08 12:20
Modified: 2015-08-08 12:00
Category: misc
Tags: test
Slug: hello-world
Authors: shinbo91
Summary: blog post test

This is the content of Hello world.
```

在完成文章撰寫後, 在 shell 中執行

```
$ make html
```

即可在 myblog/output 的對應目錄下, 看到 [Pelican][] 所產生的 Blog 的相關檔案。

若是在 shell 中輸入下列指令, 可在本地端建立一個 http://localhost:8000 的 Web Server 供測試使用。

```
$ make devserver
```

若是要停止, 則執行

```
$ ./develop_server.sh stop
```

# GitHub

若是要將 [Pelican][] 產生的 Blog 放到 [GitHub][] 上，則是利用 User Page 來達成。
只要將 [Pelican][] 所產生的 output 目錄，將目錄下的檔案放到 http://github.com/username/username.github.io.git 的 master branch 即可。

在 pip 上可安裝一支 ghp-import 程式，來簡化 output 目錄 commit 到 master branch 的動作

```
$ pip install ghp-import
```

下面為從無到有的執行的步驟:

```
cd /path/to/myblog
git init
git remote add origin https://github.com/username/username.github.io.git
git checkout --orphan source
make html
git add .
git commit -a -m "Initial commit"
ghp-import -b master output 
git push --all
```
之後，只要在 source branch 上編輯要 Blog 的文章，將發怖的文章內容 commit 到 master branch 並 push 上 [GitHub][] 即可

```
git checkout source
(edit md content)
make html
ghp-import output -b master
git push --all
```

----

參考資料:

- [使用 Pelican 建立 blog](http://weichengliou.github.io/blog/blog/2014/08/07/buildblog/)
- [Pelican with github pages](http://blog.nuventure.in/2014/09/18/pelican-with-github-pages/)

[Octopress]: http://octopress.org/
[Pelican]: http://blog.getpelican.com/
[Python]: https://www.python.org/
[Pelican Themes]: http://www.pelicanthemes.com/
[GitHub]: https://github.com/

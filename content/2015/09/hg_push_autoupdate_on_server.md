Title: Update changesets of server repository automatically while client pushes new changests
Date: 2015-09-01 16:30
Category: Programming
Tags: mercurial
Slug: hg_push_autoupdate_changeset
Authors: shinbo91

[Hg][] Client 從 Server 進行 Pull 動作時, 從 Server 上 Sync 下來的 Changesets 預設是不會進行 Merge 及 Update 動作.

同樣的, Client 將透過 Push 動作將 Changesets 發送至 Server 上, Server 上的 Repository 也是不會進行 Merge 及 Update 動作。
但若是 Server 有開啟 Web 介面, 則看到的會是 Client 發送 Changesets 後的最新狀態。

若是希望 Server 的 Repository 在 Client 進行 Push 動作後, 可以自動進行 Update.
則可以在 Server 的 mercurial.ini 中加入下列內容即可:

```
[hooks]
changegroup = hg update
```

參考資料:

- [Any way to 'hg push' and have an automatic 'hg update' on the remote server?](https://mercurial.selenic.com/wiki/FAQ#FAQ.2FCommonProblems.Any_way_to_.27hg_push.27_and_have_an_automatic_.27hg_update.27_on_the_remote_server.3F)

[Hg]: https://mercurial.selenic.com/

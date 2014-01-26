---
layout: post
title: "octopressインストール"
date: 2014-01-26 00:26:33 +0900
comments: false
categories: 
---

何かコンテンツが欲しいのでとりあえず書きます。
公式ドキュメントを読めばというかコマンドをその通り叩いていればインストールされます多分。

* セットアップ：[Octopress Setup](http://octopress.org/docs/setup/)
    * rubyはRVMで構築しました
    * rakeコマンドでエラーでたりしたら`bundle exec rake`とやるといいかもです
* 設定：[Configuring Octopress](http://octopress.org/docs/configuring/)
* 記事を書く：[Blogging Basics](http://octopress.org/docs/blogging/)
    * zshだと`bundle install rake new_post\["title"\]`みたいにエスケープが必要

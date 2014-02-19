---
layout: post
published: true
title: OctopressをTravis CIでデプロイするやつ
comments: false
categories: dev
---

## 概要
Github pagesで運用しているOctopressを`git push origin source`すると、Travis CI上でジェネレートからデプロイまでやってくれる。  
この仕込みをしておくと、[Prose.io](http://prose.io/)などGithubのリポジトリをいじれるツールから記事を投稿できるようになる。すごい

## 手順
[Octopress+Prose+Github+Travis CI = coders' blog - Human, not octopus](http://rogerz.github.io/blog/2013/02/21/prose-io-github-travis-ci/)の通りにします。  
なお、Step4で以下を追記します。  
```
env:
  global:
    - GIT_COMMITTER_NAME=<名前>
    - GIT_COMMITTER_EMAIL=<Eメール>
    - GIT_AUTHOR_NAME=<名前>
    - GIT_AUTHOR_EMAIL=<Eメール>
```
この設定がないと、commitできずにpushでコケてまずいです。  
参考：[Middleman で作った web サイトを Travis + GitHub pages でお手軽に運用する - tricknotesのぼうけんのしょ](http://tricknotes.hateblo.jp/entry/2013/06/17/020229)  
（Middlemanも気になる・・）

一応最初の記事の補足をしておくと、

* Step1: OctopressをGithub pagesにデプロイ
* Step2: Prose.ioの設定。Prose.io上で色々設定できるようになったりする
* Step3: Travis CIからpushするためにGithubのアクセストークンを取得する
* Step4: .travis.ymlの設定。3で取得したトークンで`travis encrypt GH_TOKEN=your_token`を叩く
* Step5: Rakefileを改造。記事とちょっと違っていたけど適宜あわせる
* Step6: sourceブランチにpushしたらTravis CIがほげほげ

## 注意
ってほどでもないけどローカルで`git pull origin source`をしておかないと、たまにローカルから記事書いた時とかコンフリクトしそうな気がする。
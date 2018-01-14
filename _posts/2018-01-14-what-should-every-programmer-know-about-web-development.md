---
layout: post
title: Webエンジニアは知った方がいいこと
tags:
    - web
    - programmer  
---
# はじめに
Webの開発を始めたきっかけは大学院での研究プロジェクトでした。
その時、初めてRailsを知り、Web開発に関する知識全然持っていない私は、ただネット上のあるガイドに従って操作したら、意味わからなく、人生初のWebアプリ（簡単なメモ帳アプリ）が出来上がりました！！！
<br/>
Railsはすごい！自分はすごい！！（謎の自己満足）
<br/>
**うん！**ちょっと待って、
このRubyとは何？
MVCは何？
DHHは何の略（大変失礼いたしました！すみません、本当にすみません！許してください！）？
などなど
知れば知るほど質問が出てくる！
<br/>
その後、RubyとRailsの勉強はもちろん、Webエンジニアとして身につける必要なスキル・技術とは何にかへの探求及びそれらスキル・技術の勉強も日々頑張り続けています。
もちろん今でも知らないことばっかりですが、一つのことは確実にわかりました！
<br/>
それは：
**Railsは確かにすごい。。。
Rubyも凄い。。。
DHHは神。。。
ですが！
自分は全然すごくないことです！**
<br/>

今日書くのはその謎の自己満足から抜け出した後、ある日にStackExchangeで見ました[「What technical details should a programmer of a web application consider before making the site public?」](https://softwareengineering.stackexchange.com/questions/46716/what-technical-details-should-a-programmer-of-a-web-application-consider-before)（Web開発者はサイトを公開する前に知っておいたほうがいいスキル・技術）です。
中の答えは当時の自分にとって非常に参考になりましたため、ここで、整理し、これからWebエンジニアになる新人プログラマへ共有いたします。
# 新人Webエンジニアは知った方がいいこと
## インタフェースとユーザー体験
- ウェブブラウザ間基準の違いを気を付けましょう！自分のサイトは多ウェブブラウザの対応はできているのかを確認しましょう。最低限テスト必要のウェブブラウザ：
    - 最新の[Gecko](https://ja.wikipedia.org/wiki/Gecko)エンジン（[Firefox](http://firefox.com/)）
    - Webkitエンジン（[Safari](http://www.apple.com/safari/), [Chrome](http://www.google.com/chrome)及びモバイル端末上のウェブブラウザ）
    - Internet Explorer(テストするためにマイクロソフト社の[Application Compatibility VPC Images](https://www.microsoft.com/en-us/download/details.aspx?id=11575)を使ます)
    - [Opera](http://www.opera.com/)

*[browsershots](http://browsershots.org/)というツールを利用して、自分のサイトは違うシステムの違うウェブブラウザでの表示状況を確認できます。

- 主流ウェブブラウザ以外を利用しているサイトユーザーのことも配慮する。例えば：ガラケー、スクリーンリーダーや検索エンジンなど。
- Staging環境を整備しよう。新機能をリリースする際に、ユーザーへの悪い影響を最小限にするために、テストやステージング環境の整備、buildの自動化、バージョン管理などはとても大事です。
- 分かりづらいのエラー情報をユーザーに表示させない。
- クローラに収集され、スパムメールが大量殺到する恐れがあるため、ユーザーのメールアドレスをプレーンテキスト形で表示しない。
- 口コミなどのユーザーコンテンツにあるリンクへ```rel="nofollow"```を追加すること。（```nofollow```についてはこちら：https://support.google.com/webmasters/answer/96569?hl=ja）。
- 悪意利用を防ぐために利用制限をかける。例えば：人の操作であることを確認するために、多くのサイトで見られるCAPTCHA。興味のある方は[こちら](https://blog.codinghorror.com/rate-limiting-and-velocity-checking/)もぜひ合わせて読んでください。
- プログレッシブエンハンスメント。ウェブ設計の概念である。以下は[ウィキ](https://ja.wikipedia.org/wiki/%E3%83%97%E3%83%AD%E3%82%B0%E3%83%AC%E3%83%83%E3%82%B7%E3%83%96%E3%82%A8%E3%83%B3%E3%83%8F%E3%83%B3%E3%82%B9%E3%83%A1%E3%83%B3%E3%83%88)からの引用です。
    - 基本となるコンテンツはすべてのウェブブラウザからアクセスできる。
    - 基本となる機能性はすべてのウェブブラウザからアクセスできる。
    - 疎なセマンティクスですべてのコンテンツがマークアップされる。
    - 拡張レイアウトは外部リンクされたCSSで提供する。
    - 拡張された振る舞いは外部リンクされた控えめなJavaScriptで提供する。
    - エンドユーザーのウェブブラウザーの好みを尊重する。
- ユーザーの重複提出を防ぐため、Post成功したら、[リダイレクト](https://en.wikipedia.org/wiki/Post/Redirect/Get)する。
- [Webアクセシビリティ](https://weba11y.jp/basics/accessibility/accessibility_index/)。（[ウェブアクセシビリティ方針策定ガイドライン](https://waic.jp/docs/jis2016/accessibility-plan-guidelines/201604/)）。

## 安全
- ネット上ウェブサイト安全に関する情報は一杯ありますが、[OWASP development guide](https://www.owasp.org/index.php/OWASP_Guide_Project)にはウェブサイトの安全に関することほぼ全て書かれています。（OWASPとはOpen Web Application Security Projectの略で、Webアプリケーションのセキュリティに関するオープンソースのコミュニティです。OWASP development guide日本語バージョンはこちら：https://www.lac.co.jp/lacwatch/people/20160324_000328.html ）。
- [SQLインジェクション](https://ja.wikipedia.org/wiki/SQL%E3%82%A4%E3%83%B3%E3%82%B8%E3%82%A7%E3%82%AF%E3%82%B7%E3%83%A7%E3%83%B3)とその対策を理解する。
- どんな時でもユーザーのインプットを信用しない（```cookies``` と ```hidden form field```も同じです。これらもユーザーインプットです！ ）。
- [レインボー攻撃](https://securityblog.jp/words/609.html)を防ぐために、saltを使ってパスワードをHash化する。（参考資料：http://www.atmarkit.co.jp/ait/articles/1110/06/news154_2.html）。
- 自分は認証システムを開発しない（超すごい方は無視してください！）。
- [クレジットカード情報処理の仕組み](https://ja.pcisecuritystandards.org/minisite/env2/)を理解する。
- SSL/HTTPSを利用する。
- [セッションハイジャック](https://ja.wikipedia.org/wiki/%E3%82%BB%E3%83%83%E3%82%B7%E3%83%A7%E3%83%B3%E3%83%8F%E3%82%A4%E3%82%B8%E3%83%A3%E3%83%83%E3%82%AF)のことを知る。
- [クロスサイトスクリプティング（XSS）](https://ja.wikipedia.org/wiki/%E3%82%AF%E3%83%AD%E3%82%B9%E3%82%B5%E3%82%A4%E3%83%88%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%97%E3%83%86%E3%82%A3%E3%83%B3%E3%82%B0)のことを知る。
- [クロスサイトリクエストフォージェリ（XSRF）](https://ja.wikipedia.org/wiki/%E3%82%AF%E3%83%AD%E3%82%B9%E3%82%B5%E3%82%A4%E3%83%88%E3%83%AA%E3%82%AF%E3%82%A8%E3%82%B9%E3%83%88%E3%83%95%E3%82%A9%E3%83%BC%E3%82%B8%E3%82%A7%E3%83%AA)のことを知る。
- [クリックジャッキング(Clickjacking)](https://ja.wikipedia.org/wiki/%E3%82%AF%E3%83%AA%E3%83%83%E3%82%AF%E3%82%B8%E3%83%A3%E3%83%83%E3%82%AD%E3%83%B3%E3%82%B0)のことを知る。
- 常にシステムと利用しているソフトを最新にする（この間HighSierraのことを忘れてくださいwww）。
- データベースconnectionは安全であることを確認する。
- 常に最新の攻撃技術と自分のシステムの貧弱性を把握する。
- [The Google Browser Security Handbook](http://code.google.com/p/browsersec/wiki/Main)を読む。
- The Web Application Hacker's Handbook見たいの本を読む。
- [最小権限の原則](https://ja.wikipedia.org/wiki/%E6%9C%80%E5%B0%8F%E6%A8%A9%E9%99%90%E3%81%AE%E5%8E%9F%E5%89%87)を考えます。サーバーを[non-root-user](https://security.stackexchange.com/questions/47576/do-simple-linux-servers-really-need-a-non-root-user-for-security-reasons)にしてみる。
- [タブナビング(Tabnabbing)](https://securityblog.jp/words/1061.html)対策としてユーザーコンテンツ内のリンクに```rel="noopener noreferrer"```と```target="_blank"```を追加する。(参考資料：https://blog.jxck.io/entries/2016-06-12/noopener.html)。

## パフォーマンス
- 仕様に応じて、キャッシュ機能を実装する。[HTML caching](https://www.mnot.net/cache_docs/)と[HTML5 Manifest](http://www.w3.org/TR/2011/WD-html5-20110525/offline.html)を合理的に利用する。
- 画像やSVGなどの最適化。
- gzip/deflateを利用して、ページを圧縮する。
- ウェブブラウザの接続数を減らすために、複数のCSSファイルやJavascriptファイルを一つにコンバインする。重複利用されている資源をgzipで圧縮する。
- [Yahoo Exceptional Performance](https://developer.yahoo.com/performance/)に載せている資料を勉強する。
- [Google page speed](https://developers.google.com/speed/pagespeed/insights/)などのツールを利用し、パフォーマンスをテストする。（こちらのサイトもおすすめです。https://www.webpagetest.org/）
- アイコンのような小さいの画像の場合[SVGスプライト](https://24ways.org/2014/an-overview-of-svg-sprite-creation-techniques/)を利用する。（参考資料：http://program-designer.xyz/svg-sprite/）
アクセス数の多いサイトにはページ内容を分割し、分割されたコンテンツを別のドメインに置くこと。（例えば画像サーバー）
- 静的コンテンツ(画像、CSS、JavaScript及びcookiesにアクセスする必要のないウェブコンテンツ)をcookiesを使わない独立のドメインの下におくべき。理由は同一のドメインとそのサブドメインのcookiesはこれらのドメイン・サブドメインにアクセスするたびに送信してしまうから。CDN（Content Delivery Network）を使うのもお勧めです。
- ウェブページのHTTPリクエスト数を最小化にする。
- テンプレートエンジンを使う。
- サイトのルートディレクトリに```favicon.ico```を置くこと（例：```/favicon.ico```）。HTMLの中に```favicon.ico```に関する記述があるかどうかと関係なく、ウェブブラウザは```favicon.ico```をリクエストする。もし```favicon.ico```は存在しなかったら、大量の```404```エラーが発生する。サーバーのバンドワイズを消耗してしまう。

## SEO
- 検索エンジンは好きなURLにする。例えば：```example.com/index.php?page=45```のかわりに```example.com/pages/45-article-title```を使う。
- 動的なコンテンツページで```#```を利用する場合、```#```のかわりに```#!```を使う。サーバー側も```$_REQUEST["_escaped_fragment_"]```を処理する必要がある。その理由は、Googleのbotは自動的に```#!```を```$_REQUEST["_escaped_fragment_"]```に変換している為です。いわゆる```./#!page=1```の場合Googleのbotは```./#!page=1```を```./?_escaped_fragments_=page=1```に変換する。（備考：通常URL```#```以後の部分はサーバーに送信されないです。AJAXの内容もGoogleに収集されるために、```#!```を使う必要がある。Googleは```#!```を```_escaped_fragment_```に変換してからサーバーにリクエストする。）またFirefoxとChromiumを利用しているユーザーに対し、```history.pushState({"foo":"bar"}, "About", "./?page=1");```コマンドを活用できます。このコマンドを使うことでページをリロードせずにURLを変更出来ますから、```#```のかわりに```?```を使っても現在の動的なコンテンツページを維持できます。（参考資料：```history.pushState```についてはこちら：https://developer.mozilla.org/ja/docs/Web/Guide/DOM/Manipulating_the_browser_history）
- ```click here```のようなリンクを使わない。
- [XML sitemap](https://www.sitemaps.org/index.html)を生成し、サイトのルートディレクトリに置くこと。
- 同一のページへ大量のリンクが貼られている場合[```<link rel="canonical" ... />```](https://webmasters.googleblog.com/2009/02/specify-your-canonical.html)を利用する。
- [Google Webmaster Tools](http://www.google.com/webmasters/)を使う。
- [Google Analytics](http://www.google.com/analytics/) を使う。
- [robots.txt](https://ja.wikipedia.org/wiki/Robots_Exclusion_Standard)とWebクローラーの仕組みを理解する。(参考資料：https://support.google.com/webmasters/answer/1061943?hl=ja)
- リダイレクト（```301 Moved Permanently```を利用する）。例えばwww.example.comをexample.comにリダイレクトする場合、```301 Moved Permanently```を使うことで、Googleのrankは違うドメインで変ってしまうことを防ぎます。

## 技術
- HTTPのことを知る。GET、POST、sessions、cookies、statelessなどなど
- [W3C specifications](http://www.w3.org/TR/)に従ってXHTML/HTMLとCSSを書く。
- ウェブブラウザはJavaScriptを処理する仕組みを理解する。
- ウェブブラウザはCSSやJavaScriptなどのリソースをロードする仕組みを理解する。
- JavaScript sandboxの仕組みを理解する。特にiframesを使いたい場合。
- JavaScriptは常に有効されているわけではないこと。
- [301と302の違い](https://www.bigoakinc.com/blog/when-to-use-a-301-vs-302-redirect/)を知る。
- 本番環境を支える技術（OS、Apache/Nginx、ファイアウォールなど）を勉強する。
- リセット・スタイルシートを試してみる。
- JavaScriptフレームワークを使う。

## Bug fixing
- コードを書く時間は20%、メンテナンスに費した時間は80%なので、コードを書く前に解決したい問題をしっかり考えましょう！
- より良いエラーハンドリングを設計しましょう。
- ユーザーが簡単にフィードバックできる窓口を設置する。
- 他人でも継続開発・メンテナンスできるために、ドキュメントをきちんと用意しましょう。
- バックアップを取る。
- バージョン管理システムを活用する。
- 受け入れテストを忘れないで。
- 問題が発生した場合、速やかに原因を特定できるように、十分なログを取りましょう。
- ログを取る際に、処理済みの例外と未処理の例外を両方取ること。

# さいごに
最後まで読んでくださった方へ感謝します。
ありがとうございます！

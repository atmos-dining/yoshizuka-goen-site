# 吉塚 ごえん サイト作業メモ

## プロジェクト概要
- 店舗: 吉塚 ごえん（魚肴酒場）
- URL: https://yoshizuka-goen.com（要設定）
- ホスティング: GitHub Pages
- リポジトリ: atmos-dining/yoshizuka-goen-site（要作成）
- ブランチ: main

## デザイン
- テーマカラー: ディープオーシャンネイビー #1a4d6e（海鮮居酒屋をイメージ）
- フォント: Noto Sans JP
- たれよしサイトと同じ構成・レイアウト

## 店舗情報
- 住所: 〒812-0045 福岡県福岡市博多区東公園2-23
- TEL: 092-292-0063
- 営業時間: 16:00〜0:00（料理L.O. 23:00、ドリンクL.O. 23:00）
  ※土・祝前日のみドリンクL.O. 23:30
- 定休日: なし（年中無休）
- 最寄り駅: 吉塚駅より徒歩3分（約163m）
- 席数: 54席（1階カウンター・2階座敷）
- 最大宴会: 50名（貸切対応20〜50名）
- お通し: 300円/人
- HotPepper: https://www.hotpepper.jp/strJ003498732/

## 特徴・コンセプト
- 地元吉塚で愛される魚肴酒場
- 対馬直送 本マグロ盛り合わせ
- 吉塚最大サイズの大きな唐揚げ
- 白味噌の炊き餃子
- もつ煮（煮込み）
- 旬の天ぷら盛り
- 日本酒・焼酎にこだわり

## ブログの仕組み
- ブログデータ: blog/posts.json（{ "posts": [...] }形式）
- 記事一覧: blog/index.html
- 記事詳細: blog/posts/post.html?slug=xxx
- 画像: images/ フォルダ

## CMS（Sveltia CMS）
- /admin でログイン
- GitHubリポジトリ atmos-dining/yoshizuka-goen-site が必要
- Cloudflare Worker（共用）: https://sveltia-cms-auth.atmos-nextgen-team.workers.dev

## TODO（初期セットアップ）
- [ ] GitHubリポジトリ atmos-dining/yoshizuka-goen-site 作成
- [ ] GitHub Pages 有効化（Settings → Pages → main / root）
- [ ] 独自ドメイン設定（CNAME ファイル追加）
- [ ] 店舗写真をJPGで images/ に追加
  - hero-goen.jpg, hero-goen1.jpg, hero-goen2.jpg, hero-goen3.jpg（ヒーロー）
  - concept-goen.jpg（コンセプト）
  - space-goen.jpg（店内）
  - topic-maguro.jpg, topic-karaage.jpg, topic-inside.jpg（名物）
  - menu-maguro.jpg, menu-karaage.jpg, menu-tempura.jpg（メニュー）
  - drink-beer.jpg, drink-nihonshu.jpg, drink-sour.jpg（ドリンク）
  - goen_icon.png（ファビコン）
- [ ] Google Analytics タグ追加（G-XXXXXXXXXX を実際のIDに変更）
- [ ] Google Search Console 設定
- [ ] スタッフをGitHubリポジトリに招待（Write権限）

## 写真について
- 現在 images/ フォルダは空（写真なし）
- 写真が揃い次第 images/ フォルダに追加する
- 画像がない場合はブラウザで背景色（#e8f0f5）が表示される

## HotPepper 情報更新（一括）
「HotPepperの内容を全ページ最新に更新して」と言えば以下URLを全部同時フェッチして各ファイルに反映する。

- 料理: https://www.hotpepper.jp/strJ003498732/food/
- ドリンク: https://www.hotpepper.jp/strJ003498732/drink/
- コース一覧: https://www.hotpepper.jp/strJ003498732/course/
- コース詳細1: https://www.hotpepper.jp/strJ003498732/course_cnod01/
- コース詳細2: https://www.hotpepper.jp/strJ003498732/course_cnod02/
- コース詳細3: https://www.hotpepper.jp/strJ003498732/course_cnod03/
- コース詳細4: https://www.hotpepper.jp/strJ003498732/course_cnod04/

対象ファイル: menu.html / drink.html / course.html / index.html（コース・メニューセクション）
※トップページ（/strJ003498732/）だけでは料理・ドリンク・コース内容は取れない。必ず上記URLを使うこと。

## GA4設定
- 全ページの G-XXXXXXXXXX を実際のGA4プロパティIDに置き換える
- 対象ファイル: index.html, menu.html, drink.html, course.html, blog/index.html, blog/posts/post.html
- コンバージョン設定: phone_click, reservation_click

## ドメイン・DNS設定
- **ドメイン:** yoshizuka-goen.com（取得済み）
- **DNS管理:** Xserver（全サイト共通）
- **CNAME ファイル:** リポジトリルートに作成済み（内容: `yoshizuka-goen.com`）
- **GitHub Pages カスタムドメイン:** Settings → Pages → Custom domain に `yoshizuka-goen.com` を入力

### Xserver DNS に追加するレコード
| タイプ | ホスト名 | 内容 |
|------|--------|------|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | atmos-dining.github.io |

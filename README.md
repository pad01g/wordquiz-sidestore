# wordquiz-sidestore

WordQuiz の iOS 版を配布する **SideStore (AltStore 互換) のソース** (GitHub Pages)。

## iPhone への登録手順

SideStore が入っていて、WireGuard の SideStore トンネルが有効になっている前提。

1. SideStore → Sources → ＋
2. 次の URL を追加する

```
https://pad01g.github.io/wordquiz-sidestore/apps.json
```

3. Browse から WordQuiz を開いて入れる

無料の Apple ID で署名されるため、**7 日ごとの更新 (Refresh) が要る**。
SideStore を開いて WireGuard を繋いでいれば、SideStore が自分で更新する。
7 日間一度も更新されないとアプリは起動しなくなる (入れ直せば戻る。学習の記録は消えない)。

## WireGuard の設定

`SideStore.conf` は SideStore が公開している WireGuard の設定そのもの
(<https://github.com/SideStore/SideStore/releases/download/0.3.1/SideStore.conf>)。
端末の中で閉じたループバック用のトンネルで、外のサーバには繋がない。
iPhone の Safari で次を開き、共有 → WireGuard で取り込む。

```
https://pad01g.github.io/wordquiz-sidestore/SideStore.conf
```

## 中身

`apps.json` と `ipa/` は `wordquiz-frontend` 側の `ios-publish` ワークフロー
(タグ `v*.*.*` の push か手動実行で起動) が生成する。**手で編集しない。**
IPA は署名していない。署名は SideStore が端末上で行う。

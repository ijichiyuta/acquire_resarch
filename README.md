# 使い方

## 全体の構成

Claude in Chrome と Claude Code は**直接つながっていません**。両者を橋渡しするのは、あなたのコピー＆ペーストとこのフォルダです。

```
[ Chrome ]  Claude in Chrome がページを読んで判定 → Markdown を出力
     ↓  コピペ
[ inbox/ ]  生の判定結果を .md で置く
     ↓
[ Terminal ]  Claude Code が検算・整形・型の更新
     ↓
[ log/ + types.md ]  資産として蓄積
```

**なぜ完全自動にしないか**: acquire.com はログインが必要で、機械的な巡回は利用規約に触れます。自分のブラウザで自分が見られるページを Claude in Chrome に読ませるのは問題ありませんが、クローラーは作らないでください。

---

## セットアップ（初回のみ）

```bash
# 好きな場所にフォルダを置く
cd ~/projects
# （このフォルダを配置）
cd acquire-screening

# Git で履歴を残しておくと、型リストの変遷が追える
git init && git add -A && git commit -m "init"

# Claude Code を起動
claude
```

Claude Code は起動時に `CLAUDE.md` を自動で読みます。最初に一度こう言っておくと確実です。

```
CLAUDE.md と criteria.md と types.md を読んで、現在の状態を要約して。
```

---

## 毎回の流れ

### ① 一覧で足切り（Chrome）

acquire.com の Browse ページを開き、`prompts/chrome-triage.md` の中身を貼る。
→ 優先度「高」の案件番号が返ってくる。

### ② 詳細を判定（Chrome）

該当リスティングを開き、**「See more」を全部展開してから** `prompts/chrome-detail.md` の中身を貼る。
→ Markdown が返ってくる。

### ③ 受け渡し

返ってきた Markdown をコピーして、`inbox/` に適当な名前で保存する。

```bash
pbpaste > inbox/$(date +%Y%m%d-%H%M).md   # macOS
```

### ④ 検算と記録（Claude Code）

```
inbox/ の新しいファイルを処理して。
criteria.md に照らして検算し直して、間違いがあれば指摘した上で
log/ に正式な記録として起こして、必要なら types.md と criteria.md を更新して。
```

Claude Code は **Chrome 側の判定を鵜呑みにしません**。計算を自分でやり直し、矛盾があれば指摘します。ここが二段構えにしている理由です。

---

## 定期的にやること（10件ごとくらい）

```
log/ を全部読んで、types.md を見直して。
似た型が重複していないか、却下すべき型が残っていないか、
新しく見えてきたパターンがないかを確認して、必要なら統合・整理して。
```

型リストは増やし続けると価値が下がります。**統合と削除を定期的に**。

---

## もっと自動化したくなったら

現状の構成で足りなくなった場合の選択肢。

**A. Claude Code から直接ブラウザを操作する**
Claude Code に Playwright MCP や Chrome DevTools MCP を接続すれば、Claude Code 自身がブラウザを動かせます。ただし acquire.com はログイン必須なので、認証の受け渡しと利用規約の両方を検討する必要があります。**まずは現行の手動運用で10件回してから**判断してください。

**B. Slack Alerts で入口を自動化する**
acquire.com には条件に合う新着を通知する機能があります。**探しに行く作業をやめる**のが一番効きます。判定はChromeで手動のままでも、全体の時間は大きく減ります。

**C. 型集めの主戦場を移す**
acquire.com は財務しか見えません。集客の手順まで書いてある Starter Story や Indie Hackers のほうが「型」の抽出源としては上です。同じ `criteria.md` と `types.md` をそのまま使えます。

---

## ファイルの役割まとめ

| ファイル | 誰が読む | 役割 |
|---|---|---|
| `CLAUDE.md` | Claude Code（自動） | 前提コンテキスト。毎回読まれる |
| `criteria.md` | Claude Code / Chrome | 判定基準の本体。更新していく |
| `types.md` | 両方 | **最重要資産**。抽出した型 |
| `log/` | Claude Code | 案件ごとの判定記録 |
| `prompts/` | あなた（コピペ元） | Chrome に貼るプロンプト |
| `inbox/` | Claude Code | Chrome の出力の受け皿。処理後は削除 |

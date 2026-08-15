# Round 5 イテレーション3 途中状態（Chrome切断時のスナップショット）

**イテレーション3完了（2026-08-15）**: 145/180判定済み。#139〜#145の7件をログ・types.md・SERVICES.md（学べる図鑑、ユーザー要望で新設）に反映しGitHubへプッシュ済み。
- 注: 収穫時#142「サブスクWeb制作$130k利益」はURL消失（候補2URLは別案件）。開いた2件（WPテーマ/AIビルダー）を#142/#143として判定し、GEO/AEO→#144、瑞デジタル郵便→#145に繰り下げ
- 報告フォーマット（ユーザー要望）: 各案件に「わかりやすく言うと」節（サービス/強み/競合優位性/開始コスト概算）を必ず含める。SERVICES.mdにも追記していく
- 次イテレーションは下記バックログから（rev≥$25k・未judged）

## 判定予定の6件（URL確保済み）

| # | 案件 | 収穫時の数字 (TTM売上/利益/価格) | URL |
|---|---|---|---|
| 139 | ジム向けフィットネストラッキング (US Connecticut) | $202k / $40k / $254.5k | https://app.acquire.com/startup/UkBkT7SV6TdWCnODdf2IRCbivqD3/euN1XLzBrSe03NSBwpHc |
| 140 | AI自動化B2B卸売流通（omnichannel wholesale） | $1.5M / $575k / $600k | https://app.acquire.com/startup/HyccRgKc4WeQ3bPYZgOCWzRsaVX2/7iwS3rcJR9HaTTrBUfvA |
| 141 | 歯科医院向けAI患者コミュニケーション | $56k / $29k / $115k | https://app.acquire.com/startup/SQFxtihHnOeqHmYWicPlgvzldzo2/CG8xZ3XVhHhPvp8H6DMJ |
| 142 | サブスク型Web制作・管理サービス（$130K TTM Profit表記） | $130k / $99k / $325k | 候補2つ: https://app.acquire.com/startup/89DdWFABUCe6SCI0pdmQUvGa4vt1/QIQgFfv3Ra7GgAz34HmM または https://app.acquire.com/startup/y0OxwwcuKhPy4HzGPP1pzAxvStg2/DYvBDatGy0Ml3cB3STLZ（開いてタイトル確認） |
| 143 | GEO/AEOマーケティングSaaS | $130k / $86k / $200k | https://app.acquire.com/startup/bUYk3LRxBeUxEpfjfsgGC9jEH7p1/j2lYeStYHTGItvdqtUFs |
| 144 | スウェーデン デジタル郵便B2B | $39k / $31k / $222k | https://app.acquire.com/startup/V0Qrvx26CYaMTeD95dGg3870J3y1/fC7MvLEiF8hufez2e6ed |

## #139 読み取り済みデータ（詳細ページ冒頭のみ）

- SaaS, US Connecticut。「30+ Years of Fit-Tech Innovation」ジム・YMCA・ウェルネスセンター向け
- ASKING $254.5k（6.3x profit / 1.3x revenue）
- 年成長率 **-20%**
- TTM売上 $202.1k / 利益 $40.4k
- **先月売上 $3.9k / 利益 $0** → 先月×12 = $46.8k vs TTM $202.1k（-77%乖離、急死中の疑い。要Customer metrics確認）
- 未読: Customer metrics（顧客数/ARR/チャーン）、Company overview、SELLING REASONING
- ページ内 window.__t に全文保存済みだったが切断でロスト。再訪して再抽出する

## 収穫済みバックログ（次イテレーション候補、rev≥$25k・未judged）

- EAプライベートネットワーク（executive assistants）: $41k / $40k / $125k
- 建設・ブルーカラー向けマーケ代理店: $322k / $55k / $89k
- Blue-Collar Job App + Recruitment（キオスク）: $2M / $280k / $4M
- Connected Fitness Platform（HW+サブスク）: $1.3M / -$200k / $1.3M
- AI Recruiting + Client Acquisition SaaS: $77k / $36k / $75k
- All-in-One Project & HR: $35k / $34k / $141k
- ウェルネスD2C（beauty/health）: $2.6M / $589k / $700k
- 金銀コインEC: $800k / $70k / $500k

## 済みキーワード（今回）: gym, lawn, security, staffing, payroll, dental
## 重複検出（観測のみ）: Salesforce WMS=#051、ペンテスト=#036 が再出現

## 再開手順

1. tabs_context_mcp でタブ確認（旧tabId 2099317604）
2. __seen/__harvest/__q/__getlinks を再注入（初期化JSはこのリポジトリの運用どおり）
3. #139のURLへ navigate → 6.5s待ち → window.__t 抽出 → Customer metrics/SELLING REASONING を読む
4. 以降 #140〜#144、140件時点で中間レビュー、types.md更新、コミット

# Kenのデンモク(REALITY 歌配信用)

REALITYの歌配信で使う、曲リスト・練習中ランキング・リクエスト受付のWebページです。

## 画面

**リスナー画面**
- 歌える曲リストの検索(ひらがな/カタカナ・全角/半角の違いを吸収)
- 練習中楽曲のランキング(リクエスト数順)
- 楽曲リクエスト(練習中の曲から選ぶ/新しい曲を入力)

**管理画面**(編集権限がある人だけに表示)
- 歌える曲の確認・追加・編集・削除
- 練習中楽曲の確認(リクエスト数つき)、歌える曲への移動
- リクエストの確認(未対応/対応済み)、未登録曲を練習中に追加
- 配信者名の設定、CSVでの一括登録

## データ

| コレクション | 項目 |
|---|---|
| `songs` | `title`(楽曲名), `artist`(アーティスト名), `jasrac`(JASRACコード), `nextone`(NexToneコード), `status`(`ready`=歌える / `practice`=練習中), `createdAt` |
| `requests` | `title`, `artist`, `songId`, `nickname`, `message`, `status`(`new` / `done`), `by`, `createdAt` |
| `settings/main` | `name`(配信者名) |

CSV一括登録の列順: `楽曲名,アーティスト名,JASRACコード,NexToneコード,区分`(区分は「歌える」か「練習中」)

## 動作環境について

現在の `index.html` は claude.ai の Artifact 上で動く版です。データの保存には claude.ai のデータベース機能(`window.claude.use("db")`)を使っているため、
GitHub Pages などで単体で開いた場合は画面は表示されますが、曲データの読み書きはできません。
一般のリスナーが使える形で公開するには、Firebase / Supabase などのデータベースにつなぎ替える必要があります。

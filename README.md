# Advent Calendar Embed Widget

外部ブログにiframeで埋め込めるアドベントカレンダーウィジェット

## 使い方

```html
<iframe
  src="https://your-domain.example/advent/index.html?title=Iuchi%20Advent%202025&year=2025&data=https%3A%2F%2Fyour-domain.example%2Fadvent%2Fdata.json&theme=auto"
  style="width:100%;max-width:820px;height:640px;border:0;overflow:hidden"
  loading="lazy"
  referrerpolicy="no-referrer-when-downgrade"
></iframe>
```

## URLパラメータ

| パラメータ | 説明 | デフォルト |
|-----------|------|-----------|
| `title` | カレンダーのタイトル | `Advent Calendar {year}` |
| `year` | 年 | 現在の年 |
| `days` | 日数（1-31） | `25` |
| `theme` | テーマ（`light`/`dark`/`auto`） | `auto` |
| `locale` | ロケール（`ja`/`en`） | `ja` |
| `tz` | タイムゾーン | `Asia/Tokyo` |
| `accent` | アクセントカラー（CSS color値） | - |
| `data` | データJSONのURL | - |
| `highlight` | ハイライトする日（1-31） | - |

### highlightパラメータの例

特定の日をハイライト表示：
```
?highlight=5
```

## データフォーマット（data.json）

```json
{
  "calendar": {
    "id": "iuchi-2025",
    "title": "Iuchi Advent 2025",
    "year": 2025,
    "timezone": "Asia/Tokyo"
  },
  "entries": [
    {
      "day": 1,
      "author": "Alice",
      "author_url": "https://blog.example.com/alice",
      "title": "Composeで作る…",
      "url": "https://blog.example.com/posts/1",
      "status": "published"
    },
    {
      "day": 2,
      "author": "Bob",
      "author_url": "https://x.com/bob",
      "title": "KMP入門",
      "url": null,
      "status": "reserved"
    },
    {
      "day": 3,
      "author": null,
      "title": null,
      "url": null,
      "status": "open"
    }
  ]
}
```

### ステータス

- `open`: 空き
- `reserved`: 予約済み
- `published`: 公開済み

## ローカル開発

```bash
python3 -m http.server 8000
```

その後、`http://localhost:8000/index.html?data=./data.json` にアクセス

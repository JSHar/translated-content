---
title: URL.hash
slug: Web/API/URL/hash
tags:
  - API
  - Hash
  - Property
  - Reference
  - URL
translation_of: Web/API/URL/hash
---
{{ APIRef("URL API") }}

{{domxref("URL")}} インターフェイスの **`hash`** プロパティは、`'#'` の後に URL のフラグメント識別子が続く {{domxref("USVString")}} を返します。

フラグメントは[パーセントデコード](/ja/docs/Glossary/percent-encoding)されていません。 URL にフラグメント識別子がない場合、このプロパティには空の文字列 `""` が含まれます。

{{AvailableInWorkers}}

## 構文

```
string = object.hash;
object.hash = string;
```

### 値

{{domxref("USVString")}}。

## 例

```html
var url = new URL('https://developer.mozilla.org/en-US/docs/Web/API/URL/href#Examples');
url.hash // '#Examples' を返します
```

## 仕様

| 仕様                                                             | 状態                 | コメント |
| ---------------------------------------------------------------- | -------------------- | -------- |
| {{SpecName('URL', '#dom-url-hash', 'URL.hash')}} | {{Spec2('URL')}} | 初期定義 |

## ブラウザーの互換性

{{Compat("api.URL.hash")}}

## 関連情報

- {{domxref("URL")}} インターフェイスに属します。

---
title: CSSMatrix
slug: Web/API/DOMMatrix
tags:
  - API
  - NeedsBrowserCompatibility
  - Reference
translation_of: Web/API/DOMMatrix
translation_of_original: Web/API/CSSMatrix
original_slug: Web/API/CSSMatrix
---
{{APIRef("CSSOM")}}{{Non-standard_header}}

**`CSSMatrix`** は、2D または 3D の変形が適用できる同次の 4x4 行列を表しています。このクラスは、ある時点で CSS Transitions モジュールレベル 3 の一部ということになっていましたが、現在のワーキングドラフトで存在しません。代わりに [`DOMMatrix`](/ja/docs/Web/API/DOMMatrix) を使用してください。

## 仕様

| 仕様                                                                                             | ステータス               | コメント                                                                |
| ------------------------------------------------------------------------------------------------ | ------------------------ | ----------------------------------------------------------------------- |
| {{SpecName('Compat', '#webkitcssmatrix-interface', 'WebKitCSSMatrix')}} | {{Spec2('Compat')}} | WebKit プレフィックス付きバージョン、`WebKitCSSMatrix` の初期の標準化。 |

## ブラウザー互換性

{{Compat("api.DOMMatrix")}}

## 関連情報

- [`MSCSSMatrix` documentation on MSDN](<https://msdn.microsoft.com/en-us/library/ie/hh772390(v=vs.85).aspx>)
- [`WebKitCSSMatrix` documentation at Safari Developer Library](https://developer.apple.com/library/safari/documentation/AudioVideo/Reference/WebKitCSSMatrixClassReference/index.html)
- [Mozilla bug 717722: implement `(WebKit)CSSMatrix()`](https://bugzilla.mozilla.org/show_bug.cgi?id=717722)

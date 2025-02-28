---
title: WeakMap.prototype.clear()
slug: >-
  conflicting/Web/JavaScript/Reference/Deprecated_and_obsolete_features_a91664716c4f7753074ac042780999e0
tags:
  - JavaScript
  - Method
  - Deprecated
  - Prototype
  - WeakMap
translation_of: Web/JavaScript/Reference/Global_Objects/WeakMap/clear
original_slug: Web/JavaScript/Reference/Global_Objects/WeakMap/clear
browser-compat: javascript.builtins.WeakMap.clear
---

{{JSRef}} {{deprecated_header}}

**`clear()`** メソッドは、 `WeakMap` オブジェクトからすべての要素を削除するために使用されていましたが、もはや ECMAScript とその実装に含まれていません。

## 構文

```js
clear()
```

## 例

### `clear` メソッドの使用

```js example-bad
var wm = new WeakMap();
var obj = {};

wm.set(obj, 'foo');
wm.set(window, 'bar');

wm.has(obj); // true
wm.has(window); // true

wm.clear();

wm.has(obj)  // false
wm.has(window)  // false
```

## 仕様書

どの標準にも含まれていません。

## ブラウザーの互換性

{{Compat}}

## 関連情報

- {{jsxref("WeakMap")}}

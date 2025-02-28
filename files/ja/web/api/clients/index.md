---
title: Clients
slug: Web/API/Clients
tags:
  - API
  - Clients
  - Interface
  - Reference
  - Service Workers
  - Service worker API
  - ServiceWorker
  - Workers
translation_of: Web/API/Clients
---
{{APIRef("Service Workers API")}}

**`Clients`** インターフェイスは、{{domxref("Client")}} オブジェクトへのアクセスを提供します。 これは、[サービスワーカー](/ja/docs/Web/API/ServiceWorker_API)内で {{domxref("ServiceWorkerGlobalScope", "self")}}`.clients` を介してアクセスします。

## メソッド

- {{domxref("Clients.get()")}}
  - : 指定された {{domxref("Client.id", "id")}} に一致する {{domxref("Client")}} の {{jsxref("Promise")}} を返します。
- {{domxref("Clients.matchAll()")}}
  - : {{domxref("Client")}} オブジェクトの配列の {{jsxref("Promise")}} を返します。 options 引数を使用すると、返されるクライアントの種類を制御できます。
- {{domxref("Clients.openWindow()")}}
  - : 指定された URL の新しいブラウザーウィンドウを開き、新しい {{domxref("WindowClient")}} の {{jsxref("Promise")}} を返します。
- {{domxref("Clients.claim()")}}
  - : アクティブなサービスワーカーが自身の {{domxref("ServiceWorkerRegistration.scope", "scope")}} 内のすべてのクライアントの {{domxref("ServiceWorkerContainer.controller", "controller")}} として自分自身を設定できるようにします。

## 例

次の例は、ユーザーが通知をクリックしたときに既存のチャットウィンドウを表示するか、新しいチャットウィンドウを作成します。

```js
addEventListener('notificationclick', event => {
  event.waitUntil(async function() {
    const allClients = await clients.matchAll({
      includeUncontrolled: true
    });

    let chatClient;

    // チャットウィンドウが既に開いているかどうかを確認します。
    for (const client of allClients) {
      const url = new URL(client.url);

      if (url.pathname == '/chat/') {
        // よし、使ってみよう！
        client.focus();
        chatClient = client;
        break;
      }
    }

    // 既存のチャットウィンドウが見つからなかった場合、
    // 新しいウィンドウを開きます。
    if (!chatClient) {
      chatClient = await clients.openWindow('/chat/');
    }

    // クライアントにメッセージを送ります。
    chatClient.postMessage("新しいチャットメッセージ！");
  }());
});
```

## 仕様

| 仕様                                                                     | 状態                                 | コメント |
| ------------------------------------------------------------------------ | ------------------------------------ | -------- |
| {{SpecName('Service Workers', '#clients', 'Clients')}} | {{Spec2('Service Workers')}} | 初期定義 |

## ブラウザーの互換性

{{Compat("api.Clients")}}

## 関連情報

- [Service worker の使用](/ja/docs/Web/API/ServiceWorker_API/Using_Service_Workers)
- [ServiceWorker の準備はできていますか？](https://jakearchibald.github.io/isserviceworkerready/)（英語）
- {{jsxref("Promise")}}

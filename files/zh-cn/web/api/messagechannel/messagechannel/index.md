---
title: MessageChannel()
slug: Web/API/MessageChannel/MessageChannel
---
{{APIRef("HTML DOM")}}

{{domxref("MessageChannel")}} 接口的 `MessageChannel()` 构造函数返回一个新的 {{domxref("MessageChannel")}} 对象，返回的对象中包含两个 {{domxref("MessagePort")}} 对象。

{{AvailableInWorkers}}

## 语法

```plain
var channel = new MessageChannel();
```

### 返回值

一个新创建的 {{domxref("MessageChannel")}} 对象。

## 例子

在下面的代码块中，你会看到一个由 {{domxref("MessageChannel()", "MessageChannel.MessageChannel")}} 构造函数创建的新 Channel. 当 IFrame 被加载后，我们使用 {{domxref("MessagePort.postMessage")}} 把 `port2` 和一条消息一起发送给 IFrame. 然后 `handleMessage` 回调响应 IFrame 发回的消息（使用 {{domxref("MessagePort.onmessage")}}），并把它渲染到页面段落中。{{domxref("MessageChannel.port1")}} 用来监听，当消息到达时，会进行处理。

```js
var channel = new MessageChannel();
var para = document.querySelector('p');

var ifr = document.querySelector('iframe');
var otherWindow = ifr.contentWindow;

ifr.addEventListener("load", iframeLoaded, false);

function iframeLoaded() {
  otherWindow.postMessage('Hello from the main page!', '*', [channel.port2]);
}

channel.port1.onmessage = handleMessage;
function handleMessage(e) {
  para.innerHTML = e.data;
}
```

要查看完整可运行的例子，参考我们在 Github 上的 [channel messaging basic demo](https://github.com/mdn/channel-messaging-basic-demo) ([在线运行](http://mdn.github.io/channel-messaging-basic-demo/))。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat("api.MessageChannel.MessageChannel")}}

## 参见

- [使用 channel messaging](/en-US/docs/Web/API/Channel_Messaging_API/Using_channel_messaging)

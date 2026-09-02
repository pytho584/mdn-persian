---
title: "MessagePort: postMessage() method"
short-title: postMessage()
slug: Web/API/MessagePort/postMessage
page-type: web-api-instance-method
browser-compat: api.MessagePort.postMessage
---

{{APIRef("Channel Messaging API")}} {{AvailableInWorkers}}

**`postMessage()`** 接口的 {{domxref("MessagePort")}} 方法会从端口发送一条消息，并可选择将对象的所有权转移到其他浏览上下文。

## 语法

```js-nolint
postMessage(message)
postMessage(message, transfer)
postMessage(message, options)
```

### 参数

- `message`
  - : 您想通过通道发送的消息。它可以是任何基本数据类型。多个数据项可以作为数组发送。

    > [!NOTE]
    > 能够相互发送消息的执行上下文不一定位于同一个[代理集群](/en-US/docs/Web/JavaScript/Reference/Execution_model#agent_clusters_and_memory_sharing)中，因此它们无法共享内存。{{jsxref("SharedArrayBuffer")}} 对象或由其支持的缓冲区视图不能跨代理集群发送。如果尝试这样做，接收端将生成一个包含 `DataCloneError` {{domxref("DOMException")}} 的 {{domxref("BroadcastChannel/messageerror_event", "messageerror")}} 事件。

- `transfer` {{optional_inline}}
  - : 一个可选的[可转移对象](/en-US/docs/Web/API/Web_Workers_API/Transferable_objects)[数组](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)，用于转移所有权。这些对象的所有权将移交给目标端，并且在发送端不再可用。这些可转移对象不会自动发送；它们必须包含在消息中，或者通过其他方式（例如通过 {{domxref("MessageEvent.ports")}} 的 {{domxref("MessagePort")}}）可供接收方访问。

- `options` {{optional_inline}}
  - : 一个可选对象，包含以下属性：
    - `transfer` {{optional_inline}}
      - : 含义与 `transfer` 参数相同。

### 返回值

无（{{jsxref("undefined")}}）。

## 示例

在以下代码块中，您可以看到使用 {{domxref("MessageChannel.MessageChannel", "MessageChannel()")}} 构造函数创建了一个新通道。当 IFrame 加载完成后，我们使用 {{domxref("window.postMessage")}} 将 {{domxref("MessageChannel.port2")}} 连同一条消息传递给 IFrame。iframe 接收消息，并通过 `postMessage()` 在 `MessageChannel` 上发回消息。然后，`handleMessage` 处理程序通过 `onmessage` 响应从 iframe 发回的消息，并将其放入一个段落中 — 监听 {{domxref("MessageChannel.port1")}} 以检查消息何时到达。

```js
const channel = new MessageChannel();
const para = document.querySelector("p");

const ifr = document.querySelector("iframe");
const otherWindow = ifr.contentWindow;

ifr.addEventListener("load", iframeLoaded);

function iframeLoaded() {
  otherWindow.postMessage("Transferring message port", "*", [channel.port2]);
}

channel.port1.onmessage = handleMessage;
function handleMessage(e) {
  para.innerHTML = e.data;
}

// in the iframe…

window.addEventListener("message", (event) => {
  const messagePort = event.ports?.[0];
  messagePort.postMessage("Hello from the iframe!");
});
```

有关完整的工作示例，请参阅 GitHub 上的[通道消息基础演示](https://github.com/mdn/dom-examples/tree/main/channel-messaging-basic)（[也可在线运行](https://mdn.github.io/dom-examples/channel-messaging-basic/)）。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [使用通道消息](/en-US/docs/Web/API/Channel_Messaging_API/Using_channel_messaging)
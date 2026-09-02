---
title: MediaSourceHandle
slug: Web/API/MediaSourceHandle
page-type: web-api-interface
browser-compat: api.MediaSourceHandle
---

{{APIRef("Media Source Extensions")}}{{AvailableInWorkers("window_and_dedicated")}}

**`MediaSourceHandle`** 接口（属于 {{domxref("Media Source Extensions API", "Media Source Extensions API", "", "nocode")}}）是 {{domxref("MediaSource")}} 的一个代理，可从专用工作线程（dedicated worker）传输回主线程，并通过其 {{domxref("HTMLMediaElement.srcObject")}} 属性附加到媒体元素。`MediaSource` 对象因是事件目标（event target）而不可转移，因此需要 `MediaSourceHandle`。

可通过 {{domxref("MediaSource.handle")}} 属性访问它。

在专用工作线程中创建的每个 `MediaSource` 对象都有其独特的 `MediaSourceHandle`。`MediaSource.handle` 获取器（getter）总是返回与关联的专用工作线程 `MediaSource` 实例对应的特定 `MediaSourceHandle` 实例。如果该 handle 已使用 {{domxref("DedicatedWorkerGlobalScope.postMessage()", "postMessage()")}} 传输到主线程，则工作线程中的 handle 实例在技术上已分离，不能再传输。

`MediaSourceHandle` 是一个[可转移对象](/en-US/docs/Web/API/Web_Workers_API/Transferable_objects)。

## 实例属性

无。

## 实例方法

无。

## 示例

可以在专用工作线程内部访问 {{domxref("MediaSource.handle", "handle")}} 属性，然后通过 {{domxref("DedicatedWorkerGlobalScope.postMessage()", "postMessage()")}} 调用将生成的 `MediaSourceHandle` 对象传输到创建该工作线程的线程（此处为主线程）：

```js
// Inside dedicated worker
let mediaSource = new MediaSource();
let handle = mediaSource.handle;
// Transfer the handle to the context that created the worker
postMessage({ arg: handle }, [handle]);

mediaSource.addEventListener("sourceopen", () => {
  // Await sourceopen on MediaSource before creating SourceBuffers
  // and populating them with fetched media — MediaSource won't
  // accept creation of SourceBuffers until it is attached to the
  // HTMLMediaElement and its readyState is "open"
});
```

在主线程中，我们通过 {{domxref("Worker.message_event", "message")}} 事件处理器接收 handle，通过其 {{domxref("HTMLMediaElement.srcObject")}} 属性将其附加到 {{htmlelement("video")}}，然后 {{domxref("HTMLMediaElement.play()", "play")}} 视频：

```js
worker.addEventListener("message", (msg) => {
  let mediaSourceHandle = msg.data.arg;
  video.srcObject = mediaSourceHandle;
  video.play();
});
```

> [!NOTE]
> `MediaSourceHandle` 无法成功传输到共享工作线程或 service worker 中，或通过它们传输。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [MSE-in-Workers Demo by Matt Wolenetz](https://wolenetz.github.io/mse-in-workers-demo/mse-in-workers-demo.html)
- {{domxref("Media Source Extensions API", "Media Source Extensions API", "", "nocode")}}
- {{domxref("MediaSource")}}
- {{domxref("SourceBuffer")}}
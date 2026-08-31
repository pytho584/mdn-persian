---
title: "AudioDecoder: flush() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioDecoder/flush"
translated_by: "n8n + AI"
---

---
title: "AudioDecoder: flush() method"
short-title: flush()
slug: Web/API/AudioDecoder/flush
page-type: web-api-instance-method
browser-compat: api.AudioDecoder.flush
---

{{securecontext_header}}{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

**`flush()`** 方法是 {{domxref("AudioDecoder")}} 接口的一个方法，它返回一个 Promise，该 Promise 在所有队列中待处理的消息完成后解析。

## Syntax

```js-nolint
flush()
```

### Parameters

无。

### Return value

一个解析为 undefined 的 {{jsxref("Promise")}}。

### Exceptions

如果发生错误，Promise 将以下列异常之一解析：

- `InvalidStateError` {{domxref("DOMException")}}
  - : 如果由于 {{domxref("AudioDecoder.state","state")}} 不是 `configured` 而导致 Promise 被拒绝，则返回该异常。

## Examples

下面的示例刷新 `AudioDecoder`。

```js
await audioDecoder.flush();
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}
---
title: "AudioDecoder: close() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioDecoder/close"
translated_by: "n8n + AI"
---

---
title: "AudioDecoder: close() method"
short-title: close()
slug: Web/API/AudioDecoder/close
page-type: web-api-instance-method
browser-compat: api.AudioDecoder.close
---

{{securecontext_header}}{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

**`close()`** 方法属于 {{domxref("AudioDecoder")}} 接口，用于结束所有待处理的工作并释放系统资源。

## 语法

```js-nolint
close()
```

### 参数

无。

### 返回值

无（{{jsxref("undefined")}}）。

## 示例

以下示例关闭了 `AudioDecoder`。

```js
AudioDecoder.close();
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}
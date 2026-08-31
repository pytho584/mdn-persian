---
title: "AudioEncoder: close() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioEncoder/close"
translated_by: "n8n + AI"
---

---
title: "AudioEncoder: close() method"
short-title: close()
slug: Web/API/AudioEncoder/close
page-type: web-api-instance-method
browser-compat: api.AudioEncoder.close
---

{{securecontext_header}}{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

**`close()`** 方法属于 {{domxref("AudioEncoder")}} 接口，用于结束所有未完成的工作并释放系统资源。

## 语法

```js-nolint
close()
```

### 参数

无。

### 返回值

无（{{jsxref("undefined")}}）。

## 示例

以下示例关闭 `AudioEncoder`。

```js
AudioEncoder.close();
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}
---
title: "PerformanceEventTiming: toJSON() method"
short-title: toJSON()
slug: Web/API/PerformanceEventTiming/toJSON
page-type: web-api-instance-method
browser-compat: api.PerformanceEventTiming.toJSON
---

{{APIRef("Performance API")}}

{{domxref("PerformanceEventTiming")}} 接口的 **`toJSON()`** 方法是一个 {{Glossary("Serialization","serializer")}}；它返回 {{domxref("PerformanceEventTiming")}} 对象的 JSON 表示。

## 语法

```js-nolint
toJSON()
```

### 参数

无。

### 返回值

一个 {{jsxref("JSON")}} 对象，它是 {{domxref("PerformanceEventTiming")}} 对象的序列化结果。

该 JSON 不包含 {{domxref("PerformanceEventTiming.target", "target")}} 属性，因为该属性的类型是 {{domxref("Node")}}，而 `Node` 不提供 `toJSON()` 操作。

## 示例

### 使用 toJSON 方法

在此示例中，调用 `entry.toJSON()` 会返回 `PerformanceEventTiming` 对象的 JSON 表示。

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    console.log(entry.toJSON());
  });
});

observer.observe({ type: "event", buffered: true });
```

上述代码会输出如下 JSON 对象：

```json
{
  "name": "dragover",
  "entryType": "event",
  "startTime": 67090751.599999905,
  "duration": 128,
  "processingStart": 67090751.70000005,
  "processingEnd": 67090751.900000095,
  "cancelable": true
}
```

要获取 JSON 字符串，你可以直接使用 [`JSON.stringify(entry)`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify)；它会自动调用 `toJSON()`。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 另请参阅

- {{jsxref("JSON")}}
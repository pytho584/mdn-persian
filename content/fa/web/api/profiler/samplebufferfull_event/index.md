---
title: "Profiler: samplebufferfull event"
short-title: samplebufferfull
slug: Web/API/Profiler/samplebufferfull_event
page-type: web-api-event
browser-compat: api.Profiler.samplebufferfull_event
---

{{APIRef("JS Self-Profiling API")}}

{{domxref("Profiler")}} 接口的 **`samplebufferfull`** 事件在 profiler 记录的样本数量达到构造函数中传入的 [`maxBufferSize`](/en-US/docs/Web/API/Profiler/Profiler#maxbuffersize) 值时触发。

该事件触发后，profiler 将不再记录任何新的样本。

此事件不可取消，也不会冒泡。

## 语法

在类似 {{domxref("EventTarget.addEventListener", "addEventListener()")}} 的方法中使用事件名称，或设置事件处理程序属性。

```js-nolint
addEventListener("samplebufferfull", (event) => { })

onsamplebufferfull = (event) => { }
```

## 事件类型

一个 {{domxref("Event")}}。

## 示例

```js
const profiler = new Profiler({ sampleInterval: 10, maxBufferSize: 100 });

profiler.addEventListener("samplebufferfull", async () => {
  console.log("Sample buffer full!");
  const trace = await profiler.stop();
  console.log(JSON.stringify(trace));
});
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}
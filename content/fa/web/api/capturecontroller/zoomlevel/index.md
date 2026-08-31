---
title: "CaptureController: zoomLevel property"
short-title: zoomLevel
slug: Web/API/CaptureController/zoomLevel
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.CaptureController.zoomLevel
---

{{APIRef("Screen Capture API")}}{{SeeCompatTable}}

{{domxref("CaptureController")}} 接口的只读属性 **`zoomLevel`** 返回所捕获显示表面的当前缩放级别。

## 值

一个数字，表示捕获显示表面的当前缩放级别。

## 示例

### 基本 `zoomLevel` 用法

在我们的实时演示中，如[使用捕获表面控制 API](/en-US/docs/Web/API/Screen_Capture_API/Captured_Surface_Control)所示，我们在控制器的 {{domxref("CaptureController.zoomlevelchange_event", "zoomlevelchange")}} 事件的事件处理函数中使用了 `zoomLevel` 属性。当事件触发时，更新后的 `zoomLevel` 会写入一个 `<output>` 元素。

```js
// Create controller and start capture
const controller = new CaptureController();
videoElem.srcObject = await navigator.mediaDevices.getDisplayMedia({
  controller,
});

// ...

controller.addEventListener(
  "zoomlevelchange",
  () => (outputElem.textContent = `${controller.zoomLevel}%`),
);
```

有关完整的工作示例，请参阅[使用捕获表面控制 API](/en-US/docs/Web/API/Screen_Capture_API/Captured_Surface_Control)。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [Screen Capture API](/en-US/docs/Web/API/Screen_Capture_API)
- {{domxref("MediaDevices.getDisplayMedia()")}}
- [使用捕获表面控制 API](/en-US/docs/Web/API/Screen_Capture_API/Captured_Surface_Control)
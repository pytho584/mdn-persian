---
title: "DevicePosture"
slug: Web/API/DevicePosture
page-type: web-api-interface
status:
  - experimental
browser-compat: api.DevicePosture
---

{{APIRef("Device Posture API")}}{{SeeCompatTable}}

**`DevicePosture`** 接口，属于 {{domxref("Device Posture API", "Device Posture API", "", "nocode")}}，表示设备的姿态，即视口处于平放状态还是折叠状态。

{{InheritanceDiagram}}

## 实例属性

_继承自其父接口 {{DOMxRef("EventTarget")}} 的属性。_

- {{domxref("DevicePosture.type", "type")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : 返回设备当前的姿态。

## 事件

- {{domxref("DevicePosture.change_event", "change")}} {{Experimental_Inline}}
  - : 当设备姿态发生变化时触发。

## 示例

```js
const postureOutput = document.getElementById("currentPosture");

function reportPostureOutput() {
  // type 属性返回 "continuous" 或 "folded"
  postureOutput.textContent = `Device posture: ${navigator.devicePosture.type}`;
}

navigator.devicePosture.addEventListener("change", reportPostureOutput);
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- CSS {{cssxref("@media/device-posture", "device-posture")}} `@media` 特性
- [Device Posture API](/en-US/docs/Web/API/Device_Posture_API)
- [可折叠 API 的源试用](https://developer.chrome.com/blog/foldable-apis-ot)（developer.chrome.com，2024）
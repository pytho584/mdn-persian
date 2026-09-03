---
title: "PositionSensorVRDevice: resetSensor() method"
short-title: resetSensor()
slug: Web/API/PositionSensorVRDevice/resetSensor
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.PositionSensorVRDevice.resetSensor
---

{{deprecated_header}}{{APIRef("WebVR API")}}{{Non-standard_header}}

**`resetSensor()`** 方法属于 {{domxref("VRDisplay")}} 接口，_可以在需要时用于重置传感器_，使位置和方向值归零。

## 语法

```js-nolint
resetSensor()
```

### 参数

无。

### 返回值

无（{{jsxref("undefined")}}）。

## 示例

下面的演示使用 WebVR API 在 {{domxref("window.requestAnimationFrame()","requestAnimationFrame")}} 循环的每一帧上更新一个简单的 {{domxref("CanvasRenderingContext2D")}} 场景视图。它除了其他功能外，还在界面中提供了一个「重置传感器」按钮，按下该按钮时会对位置传感器执行 `resetSensor()` 函数。JavaScript 代码如下：

```js
document.querySelector("button").onclick = () => {
  gPositionSensor.resetSensor();
};
```

按下按钮时，传感器/头戴式显示器的当前位置、方向等会被设为零——这使得该方法在应用首次加载时可用于校准。

## 浏览器兼容性

{{Compat}}

## 参见

- [WebVR API](/en-US/docs/Web/API/WebVR_API)
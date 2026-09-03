---
title: OrientationSensor
slug: Web/API/OrientationSensor
page-type: web-api-interface
browser-compat: api.OrientationSensor
---

{{securecontext_header}}{{APIRef("Sensor API")}}

**`OrientationSensor`** 接口是[传感器 API](/en-US/docs/Web/API/Sensor_APIs) 中方向传感器的基类。此接口不能直接使用，而是通过继承它的接口来提供属性和方法。

此功能可能被服务器上设置的[权限策略](/en-US/docs/Web/HTTP/Guides/Permissions_Policy)阻止。

{{InheritanceDiagram}}

## 基于 OrientationSensor 的接口

以下列表列出了基于 OrientationSensor 接口的接口。

- {{domxref('AbsoluteOrientationSensor')}}
- {{domxref('RelativeOrientationSensor')}}

## 实例属性

- {{domxref("OrientationSensor.quaternion")}} {{ReadOnlyInline}}
  - : 返回一个包含四个元素的 {{jsxref('Array')}}，其元素表示设备方向的单位四元数的分量。

## 实例方法

- {{domxref("OrientationSensor.populateMatrix()")}}
  - : 根据最新的传感器读数，用旋转矩阵填充给定对象。

## 示例

### 基本示例

以下示例大致基于 [Intel 的方向手机演示](https://intel.github.io/generic-sensor-demos/orientation-phone/)，它实例化了一个频率为每秒 60 次的 `AbsoluteOrientationSensor`。在每次读取时，它使用 {{domxref('OrientationSensor.quaternion')}} 旋转手机的视觉模型。

```js
const options = { frequency: 60, referenceFrame: "device" };
const sensor = new AbsoluteOrientationSensor(options);

sensor.addEventListener("reading", () => {
  // model 是在其他地方实例化的 Three.js 对象。
  model.quaternion.fromArray(sensor.quaternion).inverse();
});
sensor.addEventListener("error", (error) => {
  if (event.error.name === "NotReadableError") {
    console.log("Sensor is not available.");
  }
});
sensor.start();
```

### 权限示例

使用方向传感器需要请求多个设备传感器的权限。由于 {{domxref('Permissions')}} 接口使用 Promise，请求权限的一个好方法是使用 {{jsxref('Promise.all')}}。

```js
const sensor = new AbsoluteOrientationSensor();
Promise.all([
  navigator.permissions.query({ name: "accelerometer" }),
  navigator.permissions.query({ name: "magnetometer" }),
  navigator.permissions.query({ name: "gyroscope" }),
]).then((results) => {
  if (results.every((result) => result.state === "granted")) {
    sensor.start();
    // …
  } else {
    console.log("No permissions to use AbsoluteOrientationSensor.");
  }
});
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}
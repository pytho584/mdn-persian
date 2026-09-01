---
title: "Gyroscope: y property"
short-title: y
slug: Web/API/Gyroscope/y
page-type: web-api-instance-property
browser-compat: api.Gyroscope.y
---

{{securecontext_header}}{{APIRef("Sensor API")}}

**`y`** 只读属性属于 {{domxref("Gyroscope")}} 接口，返回一个数字，表示设备沿其 y 轴的角速度。

## 值

一个 {{jsxref('Number')}}。

## 示例

陀螺仪通常在 {{domxref('Sensor.reading_event', 'reading')}} 事件的回调中读取。在下面的示例中，每秒读取六十次。

```js
let gyroscope = new Gyroscope({ frequency: 60 });

gyroscope.addEventListener("reading", (e) => {
  console.log(`Angular velocity along the X-axis ${gyroscope.x}`);
  console.log(`Angular velocity along the Y-axis ${gyroscope.y}`);
  console.log(`Angular velocity along the Z-axis ${gyroscope.z}`);
});
gyroscope.start();
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}
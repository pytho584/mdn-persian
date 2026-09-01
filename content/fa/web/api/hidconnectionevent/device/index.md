---
title: "HIDConnectionEvent: device property"
short-title: device
slug: Web/API/HIDConnectionEvent/device
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.HIDConnectionEvent.device
---

{{securecontext_header}}{{APIRef("WebHID API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_shared")}}

{{domxref("HIDConnectionEvent")}} 接口的 **`device`** 只读属性返回与此连接事件关联的 {{domxref("HIDDevice")}}。

## 值

一个 {{domxref("HIDDevice")}}。

## 示例

以下示例为 `connect` 和 `disconnect` 事件注册监听器，然后将 {{domxref("HIDDevice.productName")}} 打印到控制台。

```js
navigator.hid.addEventListener("connect", ({ device }) => {
  console.log(`HID connected: ${device.productName}`);
});

navigator.hid.addEventListener("disconnect", ({ device }) => {
  console.log(`HID disconnected: ${device.productName}`);
});
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}
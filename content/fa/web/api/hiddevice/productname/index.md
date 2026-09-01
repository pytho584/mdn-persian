---
title: "HIDDevice: productName property"
short-title: productName
slug: Web/API/HIDDevice/productName
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.HIDDevice.productName
---

{{securecontext_header}}{{APIRef("WebHID API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_shared")}}

{{domxref("HIDDevice")}} 接口的 **`productName`** 只读属性返回已连接 HID 设备的产品名称。

## 值

一个字符串。

## 示例

以下示例通过 {{domxref("HID.getDevices()")}} 获取设备，并将 `productName` 的值记录到控制台。

```js
let devices = await navigator.hid.getDevices();
devices.forEach((device) => {
  console.log(`HID: ${device.productName}`);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
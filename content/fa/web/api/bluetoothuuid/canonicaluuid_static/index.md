---
title: "BluetoothUUID: canonicalUUID() static method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BluetoothUUID/canonicalUUID_static"
translated_by: "n8n + AI"
---

---
title: "BluetoothUUID: canonicalUUID() static method"
short-title: canonicalUUID()
slug: Web/API/BluetoothUUID/canonicalUUID_static
page-type: web-api-static-method
status:
  - experimental
browser-compat: api.BluetoothUUID.canonicalUUID_static
---

{{APIRef("Bluetooth API")}}{{SeeCompatTable}}

**`canonicalUUID()`** 静态方法属于 {{domxref("BluetoothUUID")}} 接口，在传入 16 位或 32 位 UUID 别名时返回 128 位 UUID。

## 语法

```js-nolint
BluetoothUUID.canonicalUUID(alias)
```

### 参数

- `alias`
  - : 一个包含 16 位或 32 位 UUID 别名的字符串。

### 返回值

一个 128 位 UUID。

## 示例

在以下示例中，返回由别名 `0x110A` 表示的 UUID 并打印到控制台。

```js
let result = BluetoothUUID.canonicalUUID("0x110A");
console.log(result); // "0000110a-0000-1000-8000-00805f9b34fb"
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}
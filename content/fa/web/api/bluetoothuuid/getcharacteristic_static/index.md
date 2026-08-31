---
title: "BluetoothUUID: getCharacteristic() static method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BluetoothUUID/getCharacteristic_static"
translated_by: "n8n + AI"
---

---
title: "BluetoothUUID: getCharacteristic() static method"
short-title: getCharacteristic()
slug: Web/API/BluetoothUUID/getCharacteristic_static
page-type: web-api-static-method
status:
  - experimental
browser-compat: api.BluetoothUUID.getCharacteristic_static
---

{{APIRef("Bluetooth API")}}{{SeeCompatTable}}

**`getCharacteristic()`** 是 {{domxref("BluetoothUUID")}} 接口的一个静态方法，当传入一个名称或 16 位/32 位 UUID 别名时，返回一个表示已注册特征的 UUID。

## 语法

```js-nolint
BluetoothUUID.getCharacteristic(name)
```

### 参数

- `name`
  - : 一个包含特征名称的字符串。

### 返回值

一个 128 位 UUID。

### 异常

- {{jsxref("TypeError")}}
  - : 如果 `name` 不在注册表中，则抛出该异常。

## 示例

在以下示例中，返回名为 `apparent_wind_direction` 的特征所对应的 UUID，并打印到控制台。

```js
let result = BluetoothUUID.getCharacteristic("apparent_wind_direction");
console.log(result); // "00002a73-0000-1000-8000-00805f9b34fb"
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}
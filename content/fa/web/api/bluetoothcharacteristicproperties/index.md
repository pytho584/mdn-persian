---
title: "BluetoothCharacteristicProperties"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BluetoothCharacteristicProperties"
translated_by: "n8n + AI"
---

---
title: BluetoothCharacteristicProperties
slug: Web/API/BluetoothCharacteristicProperties
page-type: web-api-interface
status:
  - experimental
browser-compat: api.BluetoothCharacteristicProperties
---

{{APIRef("Bluetooth API")}}{{securecontext_header}}{{SeeCompatTable}}

**`BluetoothCharacteristicProperties`** 接口属于 [Web Bluetooth API](/en-US/docs/Web/API/Web_Bluetooth_API)，提供给定 {{domxref('BluetoothRemoteGATTCharacteristic')}} 上有效的操作。

该接口通过调用 {{DOMxRef("BluetoothRemoteGATTCharacteristic.properties")}} 返回。

## 实例属性

- {{DOMxRef("BluetoothCharacteristicProperties.authenticatedSignedWrites","authenticatedSignedWrites")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : 返回一个 `boolean`，如果允许对特征值进行签名写入，则为 `true`。
- {{DOMxRef("BluetoothCharacteristicProperties.broadcast", "broadcast")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : 返回一个 `boolean`，如果允许使用服务器特征配置描述符广播特征值，则为 `true`。
- {{DOMxRef("BluetoothCharacteristicProperties.indicate","indicate")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : 返回一个 `boolean`，如果允许带确认的特征值指示，则为 `true`。
- {{DOMxRef("BluetoothCharacteristicProperties.notify","notify")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : 返回一个 `boolean`，如果允许不带确认的特征值通知，则为 `true`。
- {{DOMxRef("BluetoothCharacteristicProperties.read", "read")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : 返回一个 `boolean`，如果允许读取特征值，则为 `true`。
- {{DOMxRef("BluetoothCharacteristicProperties.reliableWrite","reliableWrite")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : 返回一个 `boolean`，如果允许对特征进行可靠写入，则为 `true`。
- {{DOMxRef("BluetoothCharacteristicProperties.writableAuxiliaries","writableAuxiliaries")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : 返回一个 `boolean`，如果允许对特征描述符进行可靠写入，则为 `true`。
- {{DOMxRef("BluetoothCharacteristicProperties.write","write")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : 返回一个 `boolean`，如果允许带响应的特征写入，则为 `true`。
- {{DOMxRef("BluetoothCharacteristicProperties.writeWithoutResponse","writeWithoutResponse")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : 返回一个 `boolean`，如果允许不带响应的特征写入，则为 `true`。

## 示例

以下示例展示如何判断 GATT 特征是否支持值更改通知。

```js
let device = await navigator.bluetooth.requestDevice({
  filters: [{ services: ["heart_rate"] }],
});
let gatt = await device.gatt.connect();
let service = await gatt.getPrimaryService("heart_rate");
let characteristic = await service.getCharacteristic("heart_rate_measurement");
if (characteristic.properties.notify) {
  characteristic.addEventListener(
    "characteristicvaluechanged",
    async (event) => {
      console.log(`Received heart rate measurement: ${event.target.value}`);
    },
  );
  await characteristic.startNotifications();
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}
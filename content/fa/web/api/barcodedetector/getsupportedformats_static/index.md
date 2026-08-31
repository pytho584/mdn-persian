---
title: "BarcodeDetector: getSupportedFormats() static method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BarcodeDetector/getSupportedFormats_static"
translated_by: "n8n + AI"
---

---
title: "BarcodeDetector: getSupportedFormats() static method"
short-title: getSupportedFormats()
slug: Web/API/BarcodeDetector/getSupportedFormats_static
page-type: web-api-static-method
status:
  - experimental
browser-compat: api.BarcodeDetector.getSupportedFormats_static
---

{{securecontext_header}}{{APIRef("Barcode Detector API")}}{{AvailableInWorkers}}{{SeeCompatTable}}

**`getSupportedFormats()`** 静态方法
属于 {{domxref("BarcodeDetector")}} 接口，返回一个 {{jsxref('Promise')}}，
该 Promise 兑现为一个包含受支持的条码格式类型的 {{jsxref('Array')}}。

## 语法

```js-nolint
BarcodeDetector.getSupportedFormats()
```

### 参数

无。

### 返回值

一个 {{jsxref('Promise')}}，兑现为一个包含
[受支持的条码格式类型](/en-US/docs/Web/API/Barcode_Detection_API#supported_barcode_formats) 的 {{jsxref('Array')}}。

### 异常

不会抛出异常。

## 示例

以下示例调用了 `getSupportedFormats()` 静态方法，并将结果记录到控制台。

```js
// 检查受支持的类型
BarcodeDetector.getSupportedFormats().then((supportedFormats) => {
  supportedFormats.forEach((format) => console.log(format));
});
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}
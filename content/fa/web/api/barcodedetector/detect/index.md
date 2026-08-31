---
title: "BarcodeDetector: detect() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BarcodeDetector/detect"
translated_by: "n8n + AI"
---

---
title: "BarcodeDetector: detect() method"
short-title: detect()
slug: Web/API/BarcodeDetector/detect
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.BarcodeDetector.detect
---

{{securecontext_header}}{{APIRef("Barcode Detector API")}}{{AvailableInWorkers}}{{SeeCompatTable}}

**`detect()`** 方法属于 {{domxref("BarcodeDetector")}} 接口，返回一个 {{jsxref('Promise')}}，该 Promise 会以一个包含图像中检测到的条形码的 {{jsxref('Array')}} 来兑现。

## 语法

```js-nolint
detect(imageBitmapSource)
```

### 参数

- `imageBitmapSource`
  - : 接收一个图像源作为参数。它可以是一个 {{domxref("HTMLImageElement")}}、一个 {{domxref("SVGImageElement")}}、一个 {{domxref("HTMLVideoElement")}}、一个 {{domxref("HTMLCanvasElement")}}、一个 {{domxref("ImageBitmap")}}、一个 {{domxref("OffscreenCanvas")}}、一个 {{domxref("VideoFrame")}}、一个类型为图像的 {{domxref('Blob')}} 或一个 {{domxref('ImageData')}} 对象。

### 返回值

返回一个 {{jsxref('Promise')}}，该 Promise 会以一个包含 `DetectedBarcode` 对象的数组来兑现，每个对象具有以下属性：

- `boundingBox`
  - : 一个 {{domxref('DOMRectReadOnly')}}，返回一个表示检测到的条形码范围的矩形尺寸，并与图像对齐。
- `cornerPoints`
  - : 检测到的条形码相对于图像的四个角点的 x 和 y 坐标，从左上角开始按顺时针顺序排列。由于图像中的透视畸变，该形状可能不是正方形。
- `format`
  - : 检测到的条形码格式。（有关完整格式列表，请参阅[支持的条形码格式](/en-US/docs/Web/API/Barcode_Detection_API#supported_barcode_formats)。）
- `rawValue`
  - : 从条形码数据解码出的字符串。

### 异常

- {{jsxref("TypeError")}}
  - : 如果未指定参数或参数 `type` 不是 `ImageBitmapSource` 类型，则抛出此异常。
- `SecurityError` {{domxref("DOMException")}}
  - : 如果 `imageBitmapSource` 有源且与文档的源不同，或者 `imageBitmapSource` 是一个 {{domxref('HTMLCanvasElement')}} 且其 [origin-clean](https://html.spec.whatwg.org/multipage/canvas.html#concept-canvas-origin-clean) 标志设置为 `false`，则抛出此异常。
- `InvalidStateError` {{domxref("DOMException")}}
  - : 如果 `imageBitmapSource` 是一个 {{domxref('HTMLImageElement')}} 且尚未完全解码或解码失败，或者是一个 {{domxref('HTMLVideoElement')}} 且其 {{domxref('HTMLMediaElement.readyState', 'readyState')}} 为 `HAVE_NOTHING` 或 `HAVE_METADATA`，则抛出此异常。

## 示例

此示例使用 `detect()` 方法检测给定图像中的条形码。然后遍历这些条形码并将条形码数据记录到控制台。

```js
barcodeDetector
  .detect(imageEl)
  .then((barcodes) => {
    barcodes.forEach((barcode) => console.log(barcode.rawValue));
  })
  .catch((err) => {
    console.error(err);
  });
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}
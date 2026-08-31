---
title: "BrowserCaptureMediaStreamTrack: cropTo() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BrowserCaptureMediaStreamTrack/cropTo"
translated_by: "n8n + AI"
---

---
title: "BrowserCaptureMediaStreamTrack: cropTo() method"
short-title: cropTo()
slug: Web/API/BrowserCaptureMediaStreamTrack/cropTo
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.BrowserCaptureMediaStreamTrack.cropTo
---

{{APIRef("Screen Capture API")}}{{SeeCompatTable}}{{securecontext_header}}

{{domxref("BrowserCaptureMediaStreamTrack")}} 接口的 **`cropTo()`** 方法会将自捕获流裁剪到指定 DOM 元素渲染的区域。

## 语法

```js-nolint
cropTo(cropTarget)
```

### 参数

- `cropTarget`
  - : 一个 {{domxref("CropTarget")}} 实例，表示流应裁剪到的元素渲染区域，或 `null`/`undefined`，在这种情况下，之前设置的任何裁剪都会从轨道中移除。

### 返回值

一个解析为 {{jsxref("undefined")}} 的 {{jsxref("Promise")}}。

该 promise 将在以下情况下拒绝：

- 轨道的 [`kind`](/en-US/docs/Web/API/MediaStreamTrack/kind) 不是 `"video"`，或其 [`readyState`](/en-US/docs/Web/API/MediaStreamTrack/readyState) 不是 `"live"`。
- 裁剪目标元素不再存在。
- 被裁剪的轨道不是从用户屏幕捕获的轨道。
- `cropTarget` 不是 {{domxref("CropTarget")}} 实例、`null` 或 `undefined`。
- `cropTarget` 是在被捕获标签页之外的标签页中创建的。

> [!NOTE]
> 在 Chromium 中，如果轨道有克隆，`cropTo()` 将拒绝（请参见 [Chrome issue 41482026](https://crbug.com/41482026)）。

## 示例

### 基本裁剪示例

```js
// Options for getDisplayMedia()
const displayMediaOptions = {
  preferCurrentTab: true,
};

// Create crop target from DOM element
const demoElem = document.querySelector("#demo");
const cropTarget = await CropTarget.fromElement(demoElem);

// Capture video stream from user's webcam and isolate video track
const stream =
  await navigator.mediaDevices.getDisplayMedia(displayMediaOptions);
const [track] = stream.getVideoTracks();

// Crop video track
await track.cropTo(cropTarget);

// Broadcast cropped stream in <video> element
videoElem.srcObject = stream;
```

有关上下文示例代码，请参阅 [使用 Element Capture 和 Region Capture API](/en-US/docs/Web/API/Screen_Capture_API/Element_Region_Capture)。

### 停止裁剪

你可以通过对先前已裁剪的轨道调用 `cropTo()` 并向其传递 `null` 参数来停止裁剪：

```js
// Stop cropping
await track.cropTo(null);
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [Screen Capture API](/en-US/docs/Web/API/Screen_Capture_API)
- [使用 Element Capture 和 Region Capture API](/en-US/docs/Web/API/Screen_Capture_API/Element_Region_Capture)
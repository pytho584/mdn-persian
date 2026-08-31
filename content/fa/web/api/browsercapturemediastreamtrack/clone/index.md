---
title: "BrowserCaptureMediaStreamTrack: clone() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BrowserCaptureMediaStreamTrack/clone"
translated_by: "n8n + AI"
---

---
title: "BrowserCaptureMediaStreamTrack: clone() method"
short-title: clone()
slug: Web/API/BrowserCaptureMediaStreamTrack/clone
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.BrowserCaptureMediaStreamTrack.clone
---

{{APIRef("Screen Capture API")}}{{SeeCompatTable}}{{securecontext_header}}

**`clone()`** 方法是 {{domxref("BrowserCaptureMediaStreamTrack")}} 接口的一个方法，用于返回原始 `BrowserCaptureMediaStreamTrack` 的克隆。

此方法在功能上与 {{domxref("MediaStreamTrack.clone()")}} 相同，不同之处在于它处理了轨道已应用裁剪或限制的情况。返回的克隆与原始 `BrowserCaptureMediaStreamTrack` 相同，但移除了任何裁剪或限制。

> [!NOTE]
> 在 Chromium 中，如果轨道有克隆，则其 {{domxref("BrowserCaptureMediaStreamTrack.cropTo", "cropTo()")}} 和 {{domxref("BrowserCaptureMediaStreamTrack.restrictTo", "restrictTo()")}} 方法将被拒绝（参见 [Chrome issue 41482026](https://crbug.com/41482026)）。

## 语法

```js-nolint
clone()
```

### 参数

无。

### 返回值

一个 {{domxref("BrowserCaptureMediaStreamTrack")}} 实例。

## 示例

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

// Create uncropped clone of the track
const clonedTrack = track.clone();
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [屏幕捕获 API](/en-US/docs/Web/API/Screen_Capture_API)
- [使用元素捕获和区域捕获 API](/en-US/docs/Web/API/Screen_Capture_API/Element_Region_Capture)
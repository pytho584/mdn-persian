---
title: "CanvasCaptureMediaStreamTrack"
source: "https://developer.mozilla.org/en-US/docs/Web/API/CanvasCaptureMediaStreamTrack"
translated_by: "n8n + AI"
---

---
title: CanvasCaptureMediaStreamTrack
slug: Web/API/CanvasCaptureMediaStreamTrack
page-type: web-api-interface
browser-compat: api.CanvasCaptureMediaStreamTrack
---

{{APIRef("Media Capture and Streams")}}

**`CanvasCaptureMediaStreamTrack`** 接口属于 {{domxref("Media Capture and Streams API", "", "", "nocode")}}，表示在调用 {{domxref("HTMLCanvasElement.captureStream()")}} 后，从 {{HTMLElement("canvas")}} 生成的 {{domxref("MediaStream")}} 中所包含的视频轨道。

{{InheritanceDiagram}}

## 实例属性

_此接口继承其父接口 {{domxref("MediaStreamTrack")}} 的属性。_

- {{domxref("CanvasCaptureMediaStreamTrack.canvas")}} {{ReadOnlyInline}}
  - : 返回实时捕获其表面的 {{domxref("HTMLCanvasElement")}} 对象。

## 实例方法

_此接口继承其父接口 {{domxref("MediaStreamTrack")}} 的方法。_

- {{domxref("CanvasCaptureMediaStreamTrack.requestFrame()")}}
  - : 手动强制捕获一帧并发送到流中。这允许希望直接指定帧捕获时间的应用程序在调用 {{domxref("HTMLCanvasElement.captureStream", "captureStream()")}} 时指定 `frameRate` 为 0，从而实现这一点。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- {{domxref("HTMLCanvasElement.captureStream()")}} 用于开始从画布捕获帧
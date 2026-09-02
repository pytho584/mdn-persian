---
title: "MediaTrackSettings: sampleSize property"
short-title: sampleSize
slug: Web/API/MediaTrackSettings/sampleSize
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.sampleSize_constraint
---

{{APIRef("Media Capture and Streams")}}

{{domxref("MediaTrackSettings")}} 字典的 **`sampleSize`** 属性是一个整数，表示当前 {{domxref("MediaStreamTrack")}} 配置的线性采样大小（以每样本位数计）。借助它，你可以确定在调用 {{domxref("MediaDevices.getUserMedia", "getUserMedia()")}} 或 {{domxref("MediaStreamTrack.applyConstraints()")}} 时，针对你所提供的 {{domxref("MediaTrackConstraints.sampleSize")}} 属性中描述的约束，实际选用了哪个值。

如有需要，你可以通过检查调用 {{domxref("MediaDevices.getSupportedConstraints()")}} 返回的 {{domxref("MediaTrackSupportedConstraints.sampleSize")}} 的值，来判断浏览器是否支持该约束。但通常这并非必要，因为浏览器会忽略它们不认识的任何约束。

## 值

一个整数值，表示每个音频样本用多少位来表示。多年来最常用的采样大小是每样本 16 位，CD 音频等就使用该值。其他常见的采样大小有 8（用于降低带宽要求）和 24（用于高分辨率专业音频）。

轨道上的每个音频通道需要 `sampleSize` 位。这意味着一个给定样本实际使用 (`sampleSize` / 8) \* {{domxref("MediaTrackSettings.channelCount","channelCount")}} 字节的数据。例如，16 位立体声音频每样本需要 (16/8)\*2 即 4 字节。

## 示例

参见 [约束练习器](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints#example_constraint_exerciser) 示例。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- [Capabilities, constraints, and settings](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaTrackConstraints.sampleSize")}}
- {{domxref("MediaTrackSettings")}}
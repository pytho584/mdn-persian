---
title: "MediaStreamAudioDestinationNode"
slug: Web/API/MediaStreamAudioDestinationNode
page-type: web-api-interface
browser-compat: api.MediaStreamAudioDestinationNode
---

{{APIRef("Web Audio API")}}

رابط `MediaStreamAudioDestinationNode` یک مقصد صوتی را نشان می‌دهد که از یک [WebRTC](/en-US/docs/Web/API/WebRTC_API) {{domxref("MediaStream")}} با یک `AudioMediaStreamTrack` واحد تشکیل شده است و می‌تواند به روشی مشابه یک `MediaStream` که از {{domxref("MediaDevices.getUserMedia", "navigator.mediaDevices.getUserMedia()")}} به دست آمده استفاده شود.

این یک {{domxref("AudioNode")}} است که به عنوان یک مقصد صوتی عمل می‌کند و با استفاده از متد {{domxref("AudioContext.createMediaStreamDestination()")}} ساخته می‌شود.

{{InheritanceDiagram}}

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">تعداد ورودی‌ها</th>
      <td><code>1</code></td>
    </tr>
    <tr>
      <th scope="row">تعداد خروجی‌ها</th>
      <td><code>0</code></td>
    </tr>
    <tr>
      <th scope="row">تعداد کانال‌ها</th>
      <td><code>2</code></td>
    </tr>
    <tr>
      <th scope="row">حالت تعداد کانال</th>
      <td><code>"explicit"</code></td>
    </tr>
    <tr>
      <th scope="row">تفسیر تعداد کانال</th>
      <td><code>"speakers"</code></td>
    </tr>
  </tbody>
</table>

## سازنده

- {{domxref("MediaStreamAudioDestinationNode.MediaStreamAudioDestinationNode", "MediaStreamAudioDestinationNode()")}}
  - : یک نمونه جدید از شیء `MediaStreamAudioDestinationNode` ایجاد می‌کند.

## ویژگی‌های نمونه

_ویژگی‌ها را از والد خود، {{domxref("AudioNode")}}، به ارث می‌برد._

- {{domxref("MediaStreamAudioDestinationNode.stream")}}
  - : یک {{domxref("MediaStream")}} که شامل یک {{domxref("MediaStreamTrack")}} است که {{domxref("MediaStreamTrack.kind", "kind")}} آن `audio` است و تعداد کانال‌های آن با گره یکسان است. می‌توانید از این ویژگی برای دریافت یک جریان از گراف صوتی و تغذیه آن به یک ساختار دیگر، مانند یک [Media Recorder](/en-US/docs/Web/API/MediaStream_Recording_API) استفاده کنید.

## روش‌های نمونه

_متدها را از والد خود، {{domxref("AudioNode")}}، به ارث می‌برد._

## مثال

برای مشاهده کد نمونه‌ای که یک `MediaStreamAudioDestinationNode` ایجاد کرده و از آن به عنوان منبع صوتی برای ضبط استفاده می‌کند، به [`AudioContext.createMediaStreamDestination()`](/en-US/docs/Web/API/AudioContext/createMediaStreamDestination#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
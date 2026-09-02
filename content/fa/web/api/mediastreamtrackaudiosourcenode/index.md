---
title: "MediaStreamTrackAudioSourceNode"
---

---
title: MediaStreamTrackAudioSourceNode
slug: Web/API/MediaStreamTrackAudioSourceNode
page-type: web-api-interface
browser-compat: api.MediaStreamTrackAudioSourceNode
---

{{APIRef("Web Audio API")}}

رابط **`MediaStreamTrackAudioSourceNode`** نوعی {{domxref("AudioNode")}} است که منبع داده‌های صوتی گرفته‌شده از یک {{domxref("MediaStreamTrack")}} مشخص را نشان می‌دهد؛ این ترک از طریق APIهای [WebRTC](/en-US/docs/Web/API/WebRTC_API) یا [Media Capture and Streams](/en-US/docs/Web/API/Media_Capture_and_Streams_API) به دست آمده است.

خود صدا، در میان سایر گزینه‌های ممکن، می‌تواند از یک میکروفون یا دستگاه نمونه‌برداری صوتی دیگر وارد شود، یا از طریق {{domxref("RTCPeerConnection")}} دریافت شود.

یک `MediaStreamTrackAudioSourceNode` هیچ ورودی و دقیقاً یک خروجی دارد و با استفاده از متد {{domxref("AudioContext.createMediaStreamTrackSource()")}} ایجاد می‌شود. این رابط مشابه {{domxref("MediaStreamAudioSourceNode")}} است، با این تفاوت که به شما امکان می‌دهد دقیقاً ترک موردنظر را مشخص کنید، به‌جای اینکه اولین ترک صوتی جریان را به‌طور پیش‌فرض در نظر بگیرد.

{{InheritanceDiagram}}

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">تعداد ورودی‌ها</th>
      <td><code>0</code></td>
    </tr>
    <tr>
      <th scope="row">تعداد خروجی‌ها</th>
      <td><code>1</code></td>
    </tr>
    <tr>
      <th scope="row">تعداد کانال‌ها</th>
      <td>
        توسط اولین {{domxref("MediaStreamTrack")}} صوتی
        ارسال‌شده به
        متد {{domxref("AudioContext.createMediaStreamTrackSource()")}}
        که آن را ایجاد کرده است، تعریف می‌شود.
      </td>
    </tr>
  </tbody>
</table>

## سازنده

- {{domxref("MediaStreamTrackAudioSourceNode.MediaStreamTrackAudioSourceNode", "MediaStreamTrackAudioSourceNode()")}}
  - : یک نمونه شیء `MediaStreamTrackAudioSourceNode` جدید با گزینه‌های مشخص‌شده ایجاد می‌کند.

## ویژگی‌های نمونه

_رابط `MediaStreamTrackAudioSourceNode` ویژگی خاص خود را ندارد؛ با این حال، ویژگی‌های والد خود، {{domxref("AudioNode")}}، را به ارث می‌برد._

## متدهای نمونه

_متدهای والد خود، {{domxref("AudioNode")}}، را به ارث می‌برد._

## مثال

برای نمونه‌کدی که از این شیء استفاده می‌کند، [`AudioContext.createMediaStreamSource()`](/en-US/docs/Web/API/AudioContext/createMediaStreamSource#examples) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- [WebRTC API](/en-US/docs/Web/API/WebRTC_API)
- [Media Capture and Streams API (Media Streams)](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- {{domxref("MediaStreamAudioSourceNode")}}
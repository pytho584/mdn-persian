---
title: MediaStreamAudioSourceNode
slug: Web/API/MediaStreamAudioSourceNode
page-type: web-api-interface
browser-compat: api.MediaStreamAudioSourceNode
---

{{APIRef("Web Audio API")}}

رابط **`MediaStreamAudioSourceNode`** نوعی {{domxref("AudioNode")}} است که به عنوان یک منبع صوتی عمل می‌کند و رسانهٔ آن از یک {{domxref("MediaStream")}} دریافت می‌شود که با استفاده از APIهای WebRTC یا Media Capture and Streams به دست آمده است.

این رسانه می‌تواند از یک میکروفون (از طریق {{domxref("MediaDevices.getUserMedia", "getUserMedia()")}}) یا از یک همتا (peer) راه دور در یک تماس WebRTC (با استفاده از ردهای صوتی {{domxref("RTCPeerConnection")}}) باشد.

یک `MediaStreamAudioSourceNode` هیچ ورودی ندارد و دقیقاً یک خروجی دارد و با استفاده از متد {{domxref("AudioContext.createMediaStreamSource()")}} ساخته می‌شود.

`MediaStreamAudioSourceNode` صدا را از _اولین_ {{domxref("MediaStreamTrack")}} می‌گیرد که مقدار ویژگی {{domxref("MediaStreamTrack.kind", "kind")}} آن `audio` باشد. برای اطلاعات بیشتر درباره ترتیب ردها، به [ترتیب ردها](#track_ordering) مراجعه کنید.

تعداد کانال‌های خروجی این گره با تعداد ردهای موجود در رد صوتی انتخاب‌شده مطابقت دارد.

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
        ۲ (اما توجه داشته باشید که {{domxref("AudioNode.channelCount")}} فقط برای up-mixing و down-mixing ورودی‌های {{domxref("AudioNode")}} استفاده می‌شود و <code>MediaStreamAudioSourceNode</code> هیچ ورودی‌ای ندارد)
      </td>
    </tr>
  </tbody>
</table>

## سازنده

- {{domxref("MediaStreamAudioSourceNode.MediaStreamAudioSourceNode", "MediaStreamAudioSourceNode()")}}
  - : یک شیء نمونه جدید از `MediaStreamAudioSourceNode` با گزینه‌های مشخص‌شده ایجاد می‌کند.

## ویژگی‌های نمونه

_علاوه بر ویژگی‌های زیر، `MediaStreamAudioSourceNode` ویژگی‌های والد خود، {{domxref("AudioNode")}} را نیز به ارث می‌برد._

- {{domxref("MediaStreamAudioSourceNode.mediaStream", "mediaStream")}} {{ReadOnlyInline}}
  - : {{domxref("MediaStream")}} که هنگام ساخت این `MediaStreamAudioSourceNode` استفاده شده است.

## روش‌های نمونه

_روش‌ها را از والد خود، {{domxref("AudioNode")}} به ارث می‌برد._

## نکات استفاده

### ترتیب ردها

برای اهداف رابط `MediaStreamTrackAudioSourceNode`، ترتیب ردهای صوتی در استریم به این صورت تعیین می‌شود که ابتدا ردهایی که {{domxref("MediaStreamTrack.kind", "kind")}} آن‌ها `audio` است گرفته می‌شوند و سپس ردها بر اساس مقادیر ویژگی {{domxref("MediaStreamTrack.id", "id")}} آن‌ها، به ترتیب نقاط کد یونیکد مرتب می‌شوند (در اصل، برای شناسه‌هایی که رشته‌های عددی-الفبایی ساده هستند، به ترتیب حروف الفبا یا ترتیب واژه‌نامه‌ای).

بنابراین، **اولین** رد، ردی است که `id` آن هنگام مرتب‌سازی همه شناسه‌های ردها بر اساس نقطه کد یونیکد، در ابتدا قرار می‌گیرد.

با این حال، توجه به این نکته مهم است که قانون تعیین‌کننده این ترتیب، مدت‌ها پس از معرفی این رابط در [Web Audio API](/en-US/docs/Web/API/Web_Audio_API) اضافه شده است. بنابراین، نمی‌توانید به راحتی به مطابقت ترتیب بین دو مرورگر یا دو نسخه از یک مرورگر اعتماد کنید.

رابط {{domxref("MediaStreamTrackAudioSourceNode")}} مشابه `MediaStreamAudioSourceNode` است، اما با این تفاوت که به شما امکان می‌دهد مشخص کنید کدام رد را می‌خواهید استفاده کنید و از این طریق از این مشکل جلوگیری می‌کند.

## مثال

برای کد نمونه‌ای که از این شیء استفاده می‌کند، به [`AudioContext.createMediaStreamSource()`](/en-US/docs/Web/API/AudioContext/createMediaStreamSource#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- [WebRTC API](/en-US/docs/Web/API/WebRTC_API)
- [Media Capture and Streams API (Media Streams)](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- {{domxref("MediaStreamTrackAudioSourceNode")}}
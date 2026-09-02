---
title: MediaElementAudioSourceNode
slug: Web/API/MediaElementAudioSourceNode
page-type: web-api-interface
browser-compat: api.MediaElementAudioSourceNode
---

{{APIRef("Web Audio API")}}

رابط `MediaElementAudioSourceNode` یک منبع صوتی متشکل از یک عنصر HTML {{ htmlelement("audio") }} یا {{ htmlelement("video") }} را نشان می‌دهد. این یک {{domxref("AudioNode")}} است که به‌عنوان منبع صوتی عمل می‌کند.

یک `MediaElementAudioSourceNode` هیچ ورودی و دقیقاً یک خروجی دارد و با استفاده از متد {{domxref("AudioContext.createMediaElementSource()")}} ساخته می‌شود. تعداد کانال‌های خروجی برابر با تعداد کانال‌های صدای ارجاع‌داده‌شده توسط {{domxref("HTMLMediaElement")}} مورد استفاده در ساخت گره است، یا اگر {{domxref("HTMLMediaElement")}} صدایی نداشته باشد، برابر با ۱ است.

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
        ۲ (اما توجه کنید که {{domxref("AudioNode.channelCount")}} فقط برای بالا‌آمیختن و پایین‌آمیختن ورودی‌های {{domxref("AudioNode")}} استفاده می‌شود و <code>MediaElementAudioSourceNode</code> هیچ ورودی‌ای ندارد)
      </td>
    </tr>
  </tbody>
</table>

## سازنده

- {{domxref("MediaElementAudioSourceNode.MediaElementAudioSourceNode", "MediaElementAudioSourceNode()")}}
  - : یک نمونه جدید از شیء `MediaElementAudioSourceNode` ایجاد می‌کند.

## ویژگی‌های نمونه

_ویژگی‌های والد خود، {{domxref("AudioNode")}} را به ارث می‌برد._

- {{domxref("MediaElementAudioSourceNode.mediaElement", "mediaElement")}} {{ReadOnlyInline}}
  - : {{domxref("HTMLMediaElement")}} مورد استفاده هنگام ساخت این `MediaStreamAudioSourceNode`.

## روش‌های نمونه

_روش‌های والد خود، {{domxref("AudioNode")}} را به ارث می‌برد._

## مثال

برای کد مثال، [`AudioContext.createMediaElementSource()`](/en-US/docs/Web/API/AudioContext/createMediaElementSource#examples) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
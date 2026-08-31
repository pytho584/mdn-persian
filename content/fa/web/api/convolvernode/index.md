---
title: ConvolverNode
slug: Web/API/ConvolverNode
page-type: web-api-interface
browser-compat: api.ConvolverNode
---

{{APIRef("Web Audio API")}}

رابطهٔ `ConvolverNode` یک {{domxref("AudioNode")}} است که یک پیچیدگی خطی (Linear Convolution) روی یک {{domxref("AudioBuffer")}} مشخص انجام می‌دهد و معمولاً برای ایجاد افکت ریورب (بازتاب صدا) استفاده می‌شود. یک `ConvolverNode` همیشه دقیقاً یک ورودی و یک خروجی دارد.

> [!NOTE]
> برای اطلاعات بیشتر دربارهٔ نظریهٔ پیچیدگی خطی، مقالهٔ [Convolution در ویکی‌پدیا](https://en.wikipedia.org/wiki/Convolution) را ببینید.

{{InheritanceDiagram}}

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">تعداد ورودی‌ها</th>
      <td><code>1</code></td>
    </tr>
    <tr>
      <th scope="row">تعداد خروجی‌ها</th>
      <td><code>1</code></td>
    </tr>
    <tr>
      <th scope="row">حالت تعداد کانال‌ها</th>
      <td><code>"clamped-max"</code></td>
    </tr>
    <tr>
      <th scope="row">تعداد کانال‌ها</th>
      <td><code>1</code>، <code>2</code> یا <code>4</code></td>
    </tr>
    <tr>
      <th scope="row">تفسیر کانال‌ها</th>
      <td><code>"speakers"</code></td>
    </tr>
  </tbody>
</table>

## سازنده

- {{domxref("ConvolverNode.ConvolverNode()", "ConvolverNode()")}}
  - : یک نمونهٔ جدید از شیء `ConvolverNode` می‌سازد.

## ویژگی‌های نمونه

_ویژگی‌های والد خود، {{domxref("AudioNode")}} را به ارث می‌برد._

- {{domxref("ConvolverNode.buffer")}}
  - : یک _{{domxref("AudioBuffer")}}_ تَک‌کاناله، استریو یا ۴ کاناله که شامل پاسخ ضربه (impulse response) (احتمولاً چندکاناله) است؛ پاسخی که `ConvolverNode` برای ایجاد افکت ریورب از آن استفاده می‌کند.
- {{domxref("ConvolverNode.normalize")}}
  - : یک مقدار بولی که کنترل می‌کند آیا پاسخ ضربهٔ موجود در بافر هنگام تنظیم ویژگی `buffer` با نرمال‌سازی توان برابر (equal-power normalization) مقیاس‌دهی شود یا نه.

## روش‌های نمونه

_روش خاصی ندارد؛ روش‌های والد خود، {{domxref("AudioNode")}} را به ارث می‌برد._

## مثال‌ها

مثال زیر کاربرد پایهٔ یک AudioContext را برای ساخت گرهٔ Convolver نشان می‌دهد. برای تکمیل مثال زیر باید یک پاسخ ضربه پیدا کنید. برای مشاهدهٔ یک مثال کامل و کاربردی، نمونهٔ [HolySpaceCow](https://mdn.github.io/webaudio-examples/holy-space-cow/) ما را ببینید.

```js
let audioCtx = new window.AudioContext();

async function createReverb() {
  let convolver = audioCtx.createConvolver();

  // load impulse response from file
  let response = await fetch("path/to/impulse-response.wav");
  let arraybuffer = await response.arrayBuffer();
  convolver.buffer = await audioCtx.decodeAudioData(arraybuffer);

  return convolver;
}

// …

let reverb = await createReverb();

// someOtherAudioNode -> reverb -> destination
someOtherAudioNode.connect(reverb);
reverb.connect(audioCtx.destination);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
---
title: DynamicsCompressorNode
slug: Web/API/DynamicsCompressorNode
page-type: web-api-interface
browser-compat: api.DynamicsCompressorNode
---

{{ APIRef("Web Audio API") }}

رابطه `DynamicsCompressorNode` یک افکت فشرده‌سازی را فراهم می‌کند که صدای بلندترین بخش‌های سیگنال را کاهش می‌دهد. فشرده‌سازی می‌تواند به جلوگیری از کلیپینگ و اعوجاج هنگام ترکیب چند صدا کمک کند و همچنین در تولید موسیقی و صدای بازی برای کنترل دینامیک، شکل‌دهی تن و افکت‌های خلاقانه استفاده می‌شود. `DynamicsCompressorNode` یک {{domxref("AudioNode")}} با دقیقاً یک ورودی و یک خروجی است.

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
      <td><code>2</code></td>
    </tr>
    <tr>
      <th scope="row">تفسیر کانال‌ها</th>
      <td><code>"speakers"</code></td>
    </tr>
  </tbody>
</table>

## سازنده

- {{domxref("DynamicsCompressorNode.DynamicsCompressorNode", "DynamicsCompressorNode()")}}
  - : یک نمونه جدید از شیء `DynamicsCompressorNode` ایجاد می‌کند.

## ویژگی‌های نمونه

_ویژگی‌ها را از والد خود، {{domxref("AudioNode")}}، به ارث می‌برد._

- {{domxref("DynamicsCompressorNode.threshold")}} {{ReadOnlyInline}}
  - : یک {{domxref("AudioParam")}} از نوع [k-rate](/en-US/docs/Web/API/AudioParam#k-rate) که مقدار دسیبل بالای آستانه را نشان می‌دهد که در آن فشرده‌سازی شروع به اثر می‌کند.
- {{domxref("DynamicsCompressorNode.knee")}} {{ReadOnlyInline}}
  - : یک {{domxref("AudioParam")}} از نوع [k-rate](/en-US/docs/Web/API/AudioParam#k-rate) شامل یک مقدار دسیبل که محدوده بالای آستانه را نشان می‌دهد، جایی که منحنی به نرمی به بخش فشرده‌شده گذر می‌کند.
- {{domxref("DynamicsCompressorNode.ratio")}} {{ReadOnlyInline}}
  - : یک {{domxref("AudioParam")}} از نوع [k-rate](/en-US/docs/Web/API/AudioParam#k-rate) که میزان تغییر مورد نیاز ورودی، بر حسب دسیبل، برای یک تغییر 1 دسیبلی در خروجی را نشان می‌دهد.
- {{domxref("DynamicsCompressorNode.reduction")}} {{ReadOnlyInline}}
  - : یک `float` که میزان کاهش بهره‌ای که در حال حاضر توسط کمپرسور به سیگنال اعمال می‌شود را نشان می‌دهد.
- {{domxref("DynamicsCompressorNode.attack")}} {{ReadOnlyInline}}
  - : یک {{domxref("AudioParam")}} از نوع [k-rate](/en-US/docs/Web/API/AudioParam#k-rate) که مدت زمان لازم، بر حسب ثانیه، برای کاهش 10 دسیبلی بهره را نشان می‌دهد.
- {{domxref("DynamicsCompressorNode.release")}} {{ReadOnlyInline}}
  - : یک {{domxref("AudioParam")}} از نوع [k-rate](/en-US/docs/Web/API/AudioParam#k-rate) که مدت زمان لازم، بر حسب ثانیه، برای افزایش 10 دسیبلی بهره را نشان می‌دهد.

## متدهای نمونه

_هیچ متد خاصی ندارد؛ متدها را از والد خود، {{domxref("AudioNode")}}، به ارث می‌برد._

## مثال

کد مثال را در [`BaseAudioContext.createDynamicsCompressor()`](/en-US/docs/Web/API/BaseAudioContext/createDynamicsCompressor#examples) ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
---
title: "AudioWorklet"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioWorklet"
translated_by: "n8n + AI"
---

---
title: AudioWorklet
slug: Web/API/AudioWorklet
page-type: web-api-interface
browser-compat: api.AudioWorklet
---

{{APIRef("Web Audio API")}}{{securecontext_header}}

رابط **`AudioWorklet`** از [Web Audio API](/en-US/docs/Web/API/Web_Audio_API) برای ارائه اسکریپت‌های پردازش صوتی سفارشی که در یک رشته‌ی جداگانه اجرا می‌شوند، استفاده می‌شود تا پردازش صوتی با تأخیر بسیار کم فراهم شود.

کد worklet در زمینه اجرای سراسری {{domxref("AudioWorkletGlobalScope")}} اجرا می‌شود، با استفاده از یک رشته‌ی Web Audio جداگانه که بین worklet و سایر گره‌های صوتی مشترک است.

به نمونه‌ی `AudioWorklet` موجود در زمینه صوتی از طریق ویژگی {{domxref("BaseAudioContext.audioWorklet")}} دسترسی پیدا کنید.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

این رابط همچنین ویژگی‌های تعریف‌شده در رابط والد خود، {{domxref("Worklet")}} را به ارث می‌برد.

- {{domxref("AudioWorklet.port", "port")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : یک {{domxref("MessagePort")}} برای ارتباط ناهمگام سفارشی بین کد در رشته‌ی اصلی و محدوده‌ی سراسری یک worklet صوتی برمی‌گرداند. این امکان ارسال پیام‌های سفارشی، مانند ارسال و دریافت داده‌های کنترلی یا تنظیمات سراسری را فراهم می‌کند.

## متدهای نمونه

این رابط متدهایی را از {{domxref('Worklet')}} به ارث می‌برد. رابط `AudioWorklet` هیچ متدی از خود تعریف نمی‌کند.

## رویدادها

`AudioWorklet` هیچ رویدادی ندارد که به آن‌ها پاسخ دهد.

## مثال‌ها

برای مثال‌های کامل ایجاد گره‌های صوتی سفارشی، به {{domxref("AudioWorkletNode")}} مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("AudioWorkletGlobalScope")}} — زمینه‌ی اجرای سراسری یک `AudioWorklet`
- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)
- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- [استفاده از AudioWorklet](/en-US/docs/Web/API/Web_Audio_API/Using_AudioWorklet)
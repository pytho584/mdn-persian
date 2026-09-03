---
title: "PeriodicWave"
slug: Web/API/PeriodicWave
page-type: web-api-interface
browser-compat: api.PeriodicWave
---

{{ APIRef("Web Audio API") }}

رابط (`PeriodicWave`) **`PeriodicWave`** یک شکل موج دوره‌ای را تعریف می‌کند که می‌تواند برای شکل‌دهی به خروجی یک {{domxref("OscillatorNode")}} استفاده شود.

`PeriodicWave` هیچ ورودی یا خروجی ندارد؛ از آن برای تعریف اسیلاتورهای سفارشی هنگام فراخوانی {{domxref("OscillatorNode.setPeriodicWave()")}} استفاده می‌شود. خود `PeriodicWave` توسط {{domxref("BaseAudioContext.createPeriodicWave")}} ایجاد/بازگردانده می‌شود.

## سازنده (Constructor)

- {{domxref("PeriodicWave.PeriodicWave", "PeriodicWave()")}}
  - : یک نمونه جدید از شیء `PeriodicWave` با استفاده از مقادیر پیش‌فرض برای همه ویژگی‌ها ایجاد می‌کند. اگر می‌خواهید مقادیر ویژگی سفارشی را از ابتدا تنظیم کنید، به جای آن از متد کارخانه {{domxref("BaseAudioContext.createPeriodicWave")}} استفاده کنید.

## ویژگی‌های نمونه (Instance properties)

هیچکدام؛ همچنین `PeriodicWave` هیچ ویژگیای به ارث نمی‌برد.

## روش‌های نمونه (Instance methods)

هیچکدام؛ همچنین `PeriodicWave` هیچ روشی به ارث نمی‌برد.

## مثال

برای یک مثال ساده از کد که نحوه ایجاد یک شیء `PeriodicWave` حاوی یک موج سینوسی ساده را نشان می‌دهد، به {{domxref("BaseAudioContext.createPeriodicWave")}} مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
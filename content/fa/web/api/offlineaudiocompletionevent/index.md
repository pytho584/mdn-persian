---
title: OfflineAudioCompletionEvent
slug: Web/API/OfflineAudioCompletionEvent
page-type: web-api-interface
browser-compat: api.OfflineAudioCompletionEvent
---

{{APIRef("Web Audio API")}}

رابط کاربری `OfflineAudioCompletionEvent` در [Web Audio API](/en-US/docs/Web/API/Web_Audio_API) رویدادهایی را نشان می‌دهد که هنگام پایان پردازش یک {{domxref("OfflineAudioContext")}} رخ می‌دهند. رویداد {{domxref("OfflineAudioContext/complete_event", "complete")}} از این رابط استفاده می‌کند.

> [!NOTE]
> این رابط به‌عنوان منسوخ (deprecated) علامت‌گذاری شده است؛ همچنان به دلایل سازگاری با نسخه‌های قبلی پشتیبانی می‌شود، اما به‌زودی وقتی نسخهٔ مبتنی بر Promise از {{domxref("OfflineAudioContext.startRendering")}} در مرورگرها پشتیبانی شود، جایگزین خواهد شد و دیگر به این رابط نیازی نخواهد بود.

{{InheritanceDiagram}}

## سازنده

- {{domxref("OfflineAudioCompletionEvent.OfflineAudioCompletionEvent", "OfflineAudioCompletionEvent()")}}
  - : یک نمونهٔ جدید از شیء `OfflineAudioCompletionEvent` ایجاد می‌کند.

## ویژگی‌های نمونه

_همچنین ویژگی‌های والد خود، {{domxref("Event")}} را به ارث می‌برد._

- {{domxref("OfflineAudioCompletionEvent.renderedBuffer")}} {{ReadOnlyInline}}
  - : یک {{domxref("AudioBuffer")}} که نتیجهٔ پردازش یک {{domxref("OfflineAudioContext")}} را包含 می‌کند.

## روش‌های نمونه

_روش‌ها را از والد خود، {{domxref("Event")}}، به ارث می‌برد._

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
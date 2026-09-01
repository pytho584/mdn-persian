---
title: FontFaceSetLoadEvent
slug: Web/API/FontFaceSetLoadEvent
page-type: web-api-interface
browser-compat: api.FontFaceSetLoadEvent
---

{{APIRef("CSS Font Loading API")}}{{AvailableInWorkers}}

رابط **`FontFaceSetLoadEvent`** در [CSS Font Loading API](/en-US/docs/Web/API/CSS_Font_Loading_API) رویدادهایی را نشان می‌دهد که پس از شروع بارگذاری فونت‌ها در یک {{domxref("FontFaceSet")}} به وقوع می‌پیوندند.

رویدادها زمانی رخ می‌دهند که بارگذاری فونت‌ها آغاز شود ([`loading`](/en-US/docs/Web/API/FontFaceSet/loading_event))، به پایان برسد ([`loadingdone`](/en-US/docs/Web/API/FontFaceSet/loadingdone_event)) یا هنگام بارگذاری یکی از فونت‌ها خطایی رخ دهد ([`loadingerror`](/en-US/docs/Web/API/FontFaceSet/loadingerror_event)).

{{InheritanceDiagram}}

## سازنده

- {{domxref("FontFaceSetLoadEvent.FontFaceSetLoadEvent","FontFaceSetLoadEvent()")}}
  - : یک شیء `FontFaceSetLoadEvent` جدید ایجاد می‌کند.

## ویژگی‌های نمونه

_همچنین ویژگی‌های والد خود، {{domxref("Event")}}، را به ارث می‌برد._

- {{domxref("FontFaceSetLoadEvent.fontfaces")}} {{ReadOnlyInline}}
  - : آرایه‌ای از نمونه‌های {{domxref("FontFace")}} را برمی‌گرداند. بسته به رویداد، این آرایه شامل فونت‌هایی است که در حال بارگذاری هستند (`loading`)، با موفقیت بارگذاری شده‌اند (`loadingdone`) یا در بارگذاری آن‌ها خطایی رخ داده است (`loadingerror`).

## متدهای نمونه

_متدهای والد خود، {{domxref("Event")}}، را به ارث می‌برد._

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Document.fonts")}}
- {{domxref("WorkerGlobalScope.fonts")}}
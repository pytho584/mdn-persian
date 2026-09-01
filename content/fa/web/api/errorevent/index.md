---
title: "ErrorEvent"
---

---
title: ErrorEvent
slug: Web/API/ErrorEvent
page-type: web-api-interface
browser-compat: api.ErrorEvent
---

{{APIRef("HTML DOM")}}{{AvailableInWorkers}}

رابط **`ErrorEvent`** رویدادهایی را نشان می‌دهد که اطلاعات مربوط به خطاهای موجود در اسکریپت‌ها یا فایل‌ها را ارائه می‌دهند.

{{InheritanceDiagram}}

## سازنده

- {{domxref("ErrorEvent.ErrorEvent", "ErrorEvent()")}}
  - : یک رویداد `ErrorEvent` با پارامترهای داده‌شده ایجاد می‌کند.

## ویژگی‌های نمونه

_همچنین ویژگی‌های والد خود، {{domxref("Event")}}، را به ارث می‌برد._

- {{domxref("ErrorEvent.message")}} {{ReadOnlyInline}}
  - : رشته‌ای شامل پیام خطای انسان‌خوان که مشکل را توصیف می‌کند.
- {{domxref("ErrorEvent.filename")}} {{ReadOnlyInline}}
  - : رشته‌ای شامل نام فایل اسکریپتی که خطا در آن رخ داده است.
- {{domxref("ErrorEvent.lineno")}} {{ReadOnlyInline}}
  - : عددی صحیح شامل شمارهٔ خط در فایل اسکریپت که خطا در آن رخ داده است.
- {{domxref("ErrorEvent.colno")}} {{ReadOnlyInline}}
  - : عددی صحیح شامل شمارهٔ ستون در فایل اسکریپت که خطا در آن رخ داده است.
- {{domxref("ErrorEvent.error")}} {{ReadOnlyInline}}
  - : مقدار جاوااسکریپتی، مانند {{jsxref("Error")}} یا {{domxref("DOMException")}}، که نشان‌دهندهٔ خطای مرتبط با این رویداد است.

## روش‌های نمونه

_روش‌های والد خود، {{domxref("Event")}}، را به ارث می‌برد._

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از وب‌ورکرها](/en-US/docs/Web/API/Web_Workers_API/Using_web_workers)؛ اشیایی که به احتمال زیاد چنین رویدادی را ایجاد می‌کنند.
- {{domxref("Window")}}: رویداد {{domxref("Window/error_event", "error")}}
- {{domxref("Navigation")}}: رویداد {{domxref("Navigation/navigateerror_event", "navigateerror")}}
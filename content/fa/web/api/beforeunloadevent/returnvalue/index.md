---
title: "BeforeUnloadEvent: returnValue property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BeforeUnloadEvent/returnValue"
translated_by: "n8n + AI"
---
---
title: "BeforeUnloadEvent: returnValue property"
short-title: returnValue
slug: Web/API/BeforeUnloadEvent/returnValue
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.BeforeUnloadEvent.returnValue
---

{{APIRef("HTML DOM")}}{{deprecated_header}}

ویژگی **`returnValue`** از رابط {{domxref("BeforeUnloadEvent")}}، زمانی که به یک مقدار truthy تنظیم شود، یک گفتگوی تأیید تولیدشده توسط مرورگر را راه‌اندازی می‌کند که از کاربران می‌پرسد آیا واقعاً می‌خواهند هنگام تلاش برای بستن یا بارگذاری مجدد صفحه، یا پیمایش به جای دیگر، صفحه را ترک کنند. این کار برای کمک به جلوگیری از از دست رفتن داده‌های ذخیره‌نشده انجام می‌شود.

> [!NOTE]
> `returnValue` یک ویژگی قدیمی است، و بهترین روش این است که گفتگو را با فراخوانی {{domxref("Event.preventDefault()")}} روی شیء `BeforeUnloadEvent` راه‌اندازی کنید، در حالی که `returnValue` را نیز برای پشتیبانی از موارد قدیمی تنظیم می‌کنید. برای راهنمایی دقیق و به‌روز، به مرجع رویداد {{domxref("Window/beforeunload_event", "beforeunload")}} مراجعه کنید.

## مقدار

مقدار `returnValue` به یک رشته خالی (`""`) مقداردهی اولیه می‌شود.

تنظیم آن بر روی تقریباً هر مقدار [truthy](/en-US/docs/Glossary/Truthy) باعث می‌شود گفتگو هنگام بستن/بارگذاری مجدد صفحه راه‌اندازی شود، اما توجه داشته باشید که همچنین به [فعال‌سازی چسبنده](/en-US/docs/Glossary/Sticky_activation) نیاز دارد. به عبارت دیگر، مرورگر فقط در صورتی گفتگو را نشان می‌دهد که فریم یا هر فریم تودرتویی یک ژست کاربری یا تعامل کاربر دریافت کرده باشد. اگر کاربر هرگز با صفحه تعامل نداشته باشد، داده کاربری برای ذخیره شدن وجود ندارد، بنابراین هیچ مورد استفاده مشروعی برای گفتگو وجود ندارد.

> [!NOTE]
> یک رشته عمومی مشخص‌شده توسط مرورگر در گفتگو نمایش داده می‌شود. این رشته توسط کد صفحه وب قابل کنترل نیست.

## نمونه‌ها

برای یک نمونه بهترین روش، به صفحه مرجع رویداد {{domxref("Window/beforeunload_event", "beforeunload")}} مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
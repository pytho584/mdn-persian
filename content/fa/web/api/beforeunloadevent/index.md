```
---
title: "BeforeUnloadEvent"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BeforeUnloadEvent"
translated_by: "n8n + AI"
---

---
title: BeforeUnloadEvent
slug: Web/API/BeforeUnloadEvent
page-type: web-api-interface
browser-compat: api.BeforeUnloadEvent
---

{{APIRef("HTML DOM")}}

رابط **`BeforeUnloadEvent`** نشان‌دهندهٔ شیء رویدادِ {{domxref("Window/beforeunload_event", "beforeunload")}} است؛ این رویداد هنگامی فعال می‌شود که پنجرهٔ فعلی، سندِ دربرگیرنده و منابع مرتبط در آستانهٔ تخلیه‌شدن (unload) قرار بگیرند.

برای راهنمایی دقیق درباره استفاده از این رویداد، به صفحهٔ مرجع رویداد {{domxref("Window/beforeunload_event", "beforeunload")}} مراجعه کنید.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌ها را از والد خود، {{DOMxRef("Event")}} به ارث می‌برد._

- {{domxref("BeforeUnloadEvent.returnValue", "returnValue")}} {{Deprecated_Inline}}
  - : وقتی روی یک مقدار [truthy](/en-US/docs/Glossary/Truthy) تنظیم شود، یک گفتگوی تأیید تحت کنترل مرورگر را فعال می‌کند که هنگام تلاش کاربر برای بستن یا بارگذاری مجدد صفحه، از او می‌پرسد آیا می‌خواهد صفحه را ترک کند. این یک قابلیت قدیمی (legacy) است و بهترین روش این است که با فراخوانی `event.preventDefault()` گفتگو را فعال کنید و در عین حال `returnValue` را نیز برای پشتیبانی از موارد قدیمی تنظیم کنید.

## روش‌های نمونه

_روش‌ها را از والد خود، {{DOMxRef("Event")}} به ارث می‌برد._

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویداد {{domxref("Window/beforeunload_event", "beforeunload")}}
```
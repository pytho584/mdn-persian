---
title: HTMLAreaElement
slug: Web/API/HTMLAreaElement
page-type: web-api-interface
browser-compat: api.HTMLAreaElement
---

{{APIRef("HTML DOM")}}

رابط **`HTMLAreaElement`** ویژگی‌ها و متدهای خاصی (فراتر از آنچه از رابط معمول {{domxref("HTMLElement")}} که به صورت ارث‌بری در دسترس دارد) برای دستکاری چیدمان و نمایش عناصر {{HtmlElement("area")}} فراهم می‌کند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

ویژگی‌های والد خود {{domxref("HTMLElement")}} را به ارث می‌برد.

- {{domxref("HTMLAreaElement.alt")}}
  - : یک رشته که منعکس‌کننده ویژگی HTML [`alt`](/en-US/docs/Web/HTML/Reference/Elements/area#alt) است، حاوی متن جایگزین برای عنصر.
- {{domxref("HTMLAreaElement.coords")}}
  - : یک رشته که منعکس‌کننده ویژگی HTML [`coords`](/en-US/docs/Web/HTML/Reference/Elements/area#coords) است، حاوی مختصات برای تعریف ناحیه داغ (hot-spot).
- {{domxref("HTMLAreaElement.download")}}
  - : یک رشته نشان‌دهنده این که منبع پیوند شده قرار است دانلود شود نه این که در مرورگر نمایش داده شود. مقدار نشان‌دهنده نام پیشنهادی فایل است. اگر نام معتبر برای سیستم‌عامل زیرین نباشد، مرورگر آن را تنظیم می‌کند.
- {{domxref("HTMLAreaElement.hash")}}
  - : یک رشته حاوی شناسه قطعه (شامل علامت هش پیشرو #)، در صورت وجود، در URL ارجاع‌شده.
- {{domxref("HTMLAreaElement.host")}}
  - : یک رشته حاوی نام میزبان و پورت (اگر پورت پیش‌فرض نباشد) در URL ارجاع‌شده.
- {{domxref("HTMLAreaElement.hostname")}}
  - : یک رشته حاوی نام میزبان در URL ارجاع‌شده.
- {{domxref("HTMLAreaElement.href")}}
  - : یک رشته که منعکس‌کننده ویژگی HTML [`href`](/en-US/docs/Web/HTML/Reference/Elements/area#href) است، حاوی یک URL معتبر از یک منبع پیوند شده.
- {{domxref("HTMLAreaElement.interestForElement")}} {{experimental_inline}} {{non-standard_inline}}
  - : عنصر هدف یک فراخواننده علاقه (interest invoker) را تنظیم یا دریافت می‌کند، در مواردی که عنصر {{htmlelement("area")}} مرتبط به عنوان یک [فراخواننده علاقه](/en-US/docs/Web/API/Popover_API/Using_interest_invokers#creating_an_interest_invoker) مشخص شده است.
- {{domxref("HTMLAreaElement.noHref")}} {{deprecated_inline}}
  - : یک پرچم بولی نشان‌دهنده غیرفعال بودن (`true`) یا فعال بودن (`false`) ناحیه.
- {{domxref("HTMLAreaElement.origin")}} {{ReadOnlyInline}}
  - : یک رشته شامل خاستگاه URL، یعنی طرح (scheme)، دامنه و پورت آن را برمی‌گرداند.
- {{domxref("HTMLAreaElement.password")}}
  - : یک رشته حاوی رمز عبور مشخص‌شده قبل از نام دامنه.
- {{domxref("HTMLAreaElement.pathname")}}
  - : یک رشته حاوی جزء مسیر (path name) در صورت وجود، از URL ارجاع‌شده.
- {{domxref("HTMLAreaElement.ping")}}
  - : یک لیست از URLها که با فاصله جدا شده‌اند. وقتی پیوند دنبال شود، مرورگر درخواست‌های {{HTTPMethod("POST")}} با بدنه PING به آن URLها ارسال می‌کند.
- {{domxref("HTMLAreaElement.port")}}
  - : یک رشته حاوی جزء پورت در صورت وجود، از URL ارجاع‌شده.
- {{domxref("HTMLAreaElement.protocol")}}
  - : یک رشته حاوی جزء پروتکل (شامل دو نقطه انتهایی `':'`)، از URL ارجاع‌شده.
- {{domxref("HTMLAreaElement.referrerPolicy")}}
  - : یک رشته که منعکس‌کننده ویژگی HTML [`referrerpolicy`](/en-US/docs/Web/HTML/Reference/Elements/area#referrerpolicy) است، نشان‌دهنده این که هنگام واکشی منبع پیوند شده از کدام ارجاع‌دهنده (referrer) استفاده شود.
- {{domxref("HTMLAreaElement.rel")}}
  - : یک رشته که منعکس‌کننده ویژگی HTML [`rel`](/en-US/docs/Web/HTML/Reference/Elements/area#rel) است، نشان‌دهنده روابط سند فعلی با منبع پیوند شده.
- {{domxref("HTMLAreaElement.relList")}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMTokenList")}} که منعکس‌کننده ویژگی HTML [`rel`](/en-US/docs/Web/HTML/Reference/Elements/area#rel) است، روابط سند فعلی با منبع پیوند شده را به عنوان یک لیست از توکن‌ها نشان می‌دهد.
- {{domxref("HTMLAreaElement.search")}}
  - : یک رشته حاوی عنصر جستجو (شامل علامت سوال پیشرو `'?'`)، در صورت وجود، از URL ارجاع‌شده.
- {{domxref("HTMLAreaElement.shape")}}
  - : یک رشته که منعکس‌کننده ویژگی HTML [`shape`](/en-US/docs/Web/HTML/Reference/Elements/area#shape) است، شکل ناحیه داغ را نشان می‌دهد، محدود به مقادیر شناخته شده.
- {{domxref("HTMLAreaElement.target")}}
  - : یک رشته که منعکس‌کننده ویژگی HTML [`target`](/en-US/docs/Web/HTML/Reference/Elements/area#target) است، زمینه مرور (browsing context) برای باز کردن منبع پیوند شده را نشان می‌دهد.
- {{domxref("HTMLAreaElement.username")}}
  - : یک رشته حاوی نام کاربری مشخص‌شده قبل از نام دامنه.

## متدهای نمونه

متدهای والد خود، {{domxref("HTMLElement")}} را به ارث می‌برد.

- {{domxref("HTMLAreaElement.toString()")}}
  - : یک رشته شامل کل URL برمی‌گرداند. این یک مترادف برای {{domxref("HTMLAreaElement.href")}} است.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- عنصر HTML که این رابط را پیاده‌سازی می‌کند: {{ HTMLElement("area") }}
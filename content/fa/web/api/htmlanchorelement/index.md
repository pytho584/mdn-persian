---
title: HTMLAnchorElement
slug: Web/API/HTMLAnchorElement
page-type: web-api-interface
browser-compat: api.HTMLAnchorElement
---

{{APIRef("HTML DOM")}}

رابط (interface) **`HTMLAnchorElement`** نمایندهٔ عناصر لینک (hyperlinks) است و ویژگی‌ها و روش‌های خاصی (علاوه بر مواردی که از رابط شیء معمولی {{domxref("HTMLElement")}} به ارث می‌برد) برای دستکاری چیدمان و نمایش این عناصر فراهم می‌کند. این رابط با عنصر [`<a>`](/en-US/docs/Web/HTML/Reference/Elements/a) مطابقت دارد؛ نباید با عنصر [`<link>`](/en-US/docs/Web/HTML/Reference/Elements/link) که توسط [`HTMLLinkElement`](/en-US/docs/Web/API/HTMLLinkElement) نمایش داده می‌شود، اشتباه گرفته شود.

{{InheritanceDiagram}}

## ویژگی‌های نمونه (Instance properties)

_ویژگی‌های والد خود، {{domxref("HTMLElement")}} را به ارث می‌برد._

- {{domxref("HTMLAnchorElement.attributionSourceId")}}
  - : یک عدد صحیح غیرمنفی که شناسهٔ منبع انتساب (attribution source identifier) مورد استفاده برای [Private Click Measurement](https://privacycg.github.io/private-click-measurement/) را نشان می‌دهد. مقادیر معتبر از `0` تا `255` هستند.
- {{domxref("HTMLAnchorElement.attributionSrc")}} {{securecontext_inline}} {{deprecated_inline}} {{non-standard_inline}}
  - : ویژگی [`attributionsrc`](/en-US/docs/Web/HTML/Reference/Elements/a#attributionsrc) را در یک عنصر {{htmlelement("a")}} به صورت برنامه‌نویسی دریافت و تنظیم می‌کند و مقدار آن ویژگی را منعکس می‌کند. `attributionsrc` مشخص می‌کند که می‌خواهید مرورگر هدر {{httpheader("Attribution-Reporting-Eligible")}} را ارسال کند. در سمت سرور، این برای راه‌اندازی ارسال هدر {{httpheader("Attribution-Reporting-Register-Source")}} در پاسخ، به منظور ثبت یک منبع انتساب مبتنی بر ناوبری (navigation-based attribution source) استفاده می‌شود.
- {{domxref("HTMLAnchorElement.download")}}
  - : یک رشته (string) که نشان می‌دهد منبع لینک شده قرار است دانلود شود نه اینکه در مرورگر نمایش داده شود. مقدار آن نام پیشنهادی فایل را نشان می‌دهد. اگر نام، یک نام فایل معتبر برای سیستم‌عامل زیرین نباشد، مرورگر آن را تطبیق می‌دهد.
- {{domxref("HTMLAnchorElement.hash")}}
  - : یک رشته که شناسهٔ قطعه (fragment identifier) را شامل می‌شود، همراه با علامت هش (`#`) ابتدایی (در صورت وجود)، در URL ارجاع‌داده‌شده.
- {{domxref("HTMLAnchorElement.host")}}
  - : یک رشته که نام میزبان (hostname) و پورت (port) را (در صورتی که پورت پیش‌فرض نباشد) در URL ارجاع‌داده‌شده نشان می‌دهد.
- {{domxref("HTMLAnchorElement.hostname")}}
  - : یک رشته که نام میزبان را در URL ارجاع‌داده‌شده نشان می‌دهد.
- {{domxref("HTMLAnchorElement.href")}}
  - : یک رشته که نتیجهٔ تجزیه (parsing) ویژگی HTML [`href`](/en-US/docs/Web/HTML/Reference/Elements/a#href) نسبت به سند (document) است و یک URL معتبر از یک منبع لینک شده را شامل می‌شود.
- {{domxref("HTMLAnchorElement.hreflang")}}
  - : یک رشته که ویژگی HTML [`hreflang`](/en-US/docs/Web/HTML/Reference/Elements/a#hreflang) را منعکس می‌کند و زبان منبع لینک شده را نشان می‌دهد.
- {{domxref("HTMLAnchorElement.interestForElement")}} {{experimental_inline}} {{non-standard_inline}}
  - : عنصر هدف یک فراخوان‌کنندهٔ علاقه (interest invoker) را دریافت یا تنظیم می‌کند، در مواردی که عنصر {{htmlelement("a")}} مرتبط به عنوان یک [فراخوان‌کنندهٔ علاقه](/en-US/docs/Web/API/Popover_API/Using_interest_invokers#creating_an_interest_invoker) مشخص شده است.
- {{domxref("HTMLAnchorElement.origin")}} {{ReadOnlyInline}}
  - : یک رشته شامل مبدأ (origin) URL، یعنی طرح (scheme)، دامنه (domain) و پورت (port) آن را برمی‌گرداند.
- {{domxref("HTMLAnchorElement.password")}}
  - : یک رشته شامل رمز عبور (password) مشخص‌شده قبل از نام دامنه.
- {{domxref("HTMLAnchorElement.pathname")}}
  - : یک رشته شامل یک `/` ابتدایی و به دنبال آن مسیر (path) URL، بدون رشتهٔ جستجو (query string) یا قطعه (fragment).
- {{domxref("HTMLAnchorElement.ping")}}
  - : یک لیست از URLها که با فاصله از هم جدا شده‌اند. وقتی لینک دنبال می‌شود، مرورگر درخواست‌های {{HTTPMethod("POST")}} با بدنهٔ PING به این URLها ارسال می‌کند.
- {{domxref("HTMLAnchorElement.port")}}
  - : یک رشته که جزء پورت (port component) را در URL ارجاع‌داده‌شده نشان می‌دهد (در صورت وجود).
- {{domxref("HTMLAnchorElement.protocol")}}
  - : یک رشته که جزء پروتکل (protocol component) را شامل می‌شود، همراه با دونقطه (`:`) دنباله‌دار، در URL ارجاع‌داده‌شده.
- {{domxref("HTMLAnchorElement.referrerPolicy")}}
  - : یک رشته که ویژگی HTML [`referrerpolicy`](/en-US/docs/Web/HTML/Reference/Elements/a#referrerpolicy) را منعکس می‌کند و مشخص می‌کند از کدام referrer استفاده شود.
- {{domxref("HTMLAnchorElement.rel")}}
  - : یک رشته که ویژگی HTML [`rel`](/en-US/docs/Web/HTML/Reference/Elements/a#rel) را منعکس می‌کند و رابطهٔ شیء هدف با شیء لینک شده را مشخص می‌کند.
- {{domxref("HTMLAnchorElement.relList")}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMTokenList")}} برمی‌گرداند که ویژگی HTML [`rel`](/en-US/docs/Web/HTML/Reference/Elements/a#rel) را به صورت یک لیست از توکن‌ها منعکس می‌کند.
- {{domxref("HTMLAnchorElement.search")}}
  - : یک رشته که عنصر جستجو (search element) را شامل می‌شود، همراه با علامت سؤال (`?`) ابتدایی (در صورت وجود)، در URL ارجاع‌داده‌شده.
- {{domxref("HTMLAnchorElement.target")}}
  - : یک رشته که ویژگی HTML [`target`](/en-US/docs/Web/HTML/Reference/Elements/a#target) را منعکس می‌کند و مشخص می‌کند که منبع لینک شده کجا نمایش داده شود.
- {{domxref("HTMLAnchorElement.text")}}
  - : یک رشته که مترادف خاصیت {{domxref("Node.textContent")}} است.
- {{domxref("HTMLAnchorElement.type")}}
  - : یک رشته که ویژگی HTML [`type`](/en-US/docs/Web/HTML/Reference/Elements/a#type) را منعکس می‌کند و نوع MIME منبع لینک شده را نشان می‌دهد.
- {{domxref("HTMLAnchorElement.username")}}
  - : یک رشته شامل نام کاربری (username) مشخص‌شده قبل از نام دامنه.

### ویژگی‌های منسوخ (Obsolete properties)

- `HTMLAnchorElement.charset` {{deprecated_inline}}
  - : یک رشته که نشان‌دهندهٔ رمزگذاری نویسه (character encoding) منبع لینک شده بود.
- `HTMLAnchorElement.coords` {{deprecated_inline}}
  - : یک رشته که یک لیست از مختصات (coordinates) جدا شده با کاما را نشان می‌داد.
- `HTMLAnchorElement.name` {{deprecated_inline}}
  - : یک رشته که نام لنگر (anchor name) را نشان می‌داد.
- `HTMLAnchorElement.rev` {{deprecated_inline}}
  - : یک رشته که ویژگی HTML [`rev`](/en-US/docs/Web/HTML/Reference/Elements/a#rev) را نشان می‌داد و رابطهٔ شیء لینک با شیء هدف را مشخص می‌کرد.
- `HTMLAnchorElement.shape` {{deprecated_inline}}
  - : یک رشته که شکل ناحیهٔ فعال (active area) را نشان می‌داد.

## روش‌های نمونه (Instance methods)

_روش‌های والد خود، {{domxref("HTMLElement")}} را به ارث می‌برد._

- {{domxref("HTMLAnchorElement.toString()")}}
  - : یک رشته شامل کل URL را برمی‌گرداند. این یک مترادف برای {{domxref("HTMLAnchorElement.href")}} است، اگرچه نمی‌توان از آن برای تغییر مقدار استفاده کرد.

## مشخصات (Specifications)

{{Specifications}}

## سازگاری با مرورگر (Browser compatibility)

{{Compat}}

## همچنین ببینید (See also)

- عنصر HTML که این رابط را پیاده‌سازی می‌کند: {{HTMLElement("a")}}
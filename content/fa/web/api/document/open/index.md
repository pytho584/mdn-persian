---
title: "Document: open() method"
short-title: open()
slug: Web/API/Document/open
page-type: web-api-instance-method
browser-compat: api.Document.open
---

{{APIRef("DOM")}}

متد **`Document.open()`** یک سند را برای {{domxref("Document.write", "نوشتن", "", "1")}} باز می‌کند.

این کار عوارض جانبی خود را دارد. برای مثال:

- همهٔ شنونده‌های رویداد (event listeners) که در حال حاضر روی سند، گره‌های داخل سند، یا پنجرهٔ سند ثبت شده‌اند، حذف می‌شوند.
- همهٔ گره‌های موجود از سند حذف می‌شوند.

## نحو (Syntax)

```js-nolint
open()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

یک شیء نمونه از `Document`.

## مثال‌ها

کد سادهٔ زیر سند را باز می‌کند و محتوای آن را با چند قطعه HTML متفاوت جایگزین می‌کند و سپس دوباره آن را می‌بندد.

```js
document.open();
document.write("<p>Hello world!</p>");
document.write("<p>I am a fish</p>");
document.write("<p>The number is 42</p>");
document.close();
```

## نکات

یک فراخوانی خودکار `document.open()` زمانی رخ می‌دهد که {{domxref("document.write()")}} پس از بارگذاری صفحه فراخوانی شود.

### امنیت محتوا

این متد تابع همان [خط‌مشی مبدأ یکسان](/en-US/docs/Web/Security/Defenses/Same-origin_policy) است که سایر ویژگی‌ها از آن پیروی می‌کنند و اگر انجام این کار مبدأ سند را تغییر دهد، کار نخواهد کرد.

## نسخهٔ سه‌پارامتری document.open()

یک نسخهٔ سه‌پارامتری `document.open()` با کاربرد کمتر و ناشناخته‌تر وجود دارد که نام مستعار {{domxref("Window.open()")}} است (برای جزئیات کامل به صفحهٔ آن مراجعه کنید).

برای مثال، این فراخوانی github.com را در یک پنجرهٔ جدید باز می‌کند، در حالی که opener آن روی `null` تنظیم شده است:

```js
document.open("https://www.github.com", "", "noopener=true");
```

## نسخهٔ دوپارامتری document.open()

مرورگرها قبلاً از نسخهٔ دوپارامتری `document.open()` با امضای زیر پشتیبانی می‌کردند:

```js
document.open(type, replace);
```

که در آن `type` نوع MIME داده‌هایی را که می‌نویسید مشخص می‌کرد (مثلاً `text/html`) و `replace` اگر تنظیم می‌شد (یعنی یک رشتهٔ `"replace"`) مشخص می‌کرد که ورودی تاریخچه (history entry) برای سند جدید، ورودی تاریخچهٔ فعلی سندی که در حال نوشتن در آن هستیم را جایگزین کند.

این شکل اکنون منسوخ شده است؛ خطا ایجاد نمی‌کند، بلکه فقط به `document.open()` ارجاع می‌دهد (یعنی معادل فراخوانی آن بدون آرگومان است). رفتار جایگزینی تاریخچه اکنون همیشه انجام می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Document")}}
- {{domxref("Window.open()")}}
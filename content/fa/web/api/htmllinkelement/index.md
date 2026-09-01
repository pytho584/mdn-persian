---
title: HTMLLinkElement
slug: Web/API/HTMLLinkElement
page-type: web-api-interface
browser-compat: api.HTMLLinkElement
---

{{ APIRef("HTML DOM") }}

رابطِ **`HTMLLinkElement`** اطلاعات مرجعِ منابع خارجی و رابطه‌ی آن منابع با یک سند و بالعکس را نشان می‌دهد (مربوط به عنصر [`<link>`](/en-US/docs/Web/HTML/Reference/Elements/link) است؛ با [`<a>`](/en-US/docs/Web/HTML/Reference/Elements/a) که توسط [`HTMLAnchorElement`](/en-US/docs/Web/API/HTMLAnchorElement) نمایش داده می‌شود اشتباه نشود). این شیء تمام ویژگی‌ها و متدهای رابط {{domxref("HTMLElement")}} را به ارث می‌برد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌ها را از والد خود، {{domxref("HTMLElement")}} به ارث می‌برد._

- {{domxref("HTMLLinkElement.as")}}
  - : رشته‌ای که نوع محتوای بارگذاری‌شده توسط لینک HTML را هنگام [`rel="preload"`](/en-US/docs/Web/HTML/Reference/Attributes/rel/preload) یا [`rel="modulepreload"`](/en-US/docs/Web/HTML/Reference/Attributes/rel/modulepreload) نشان می‌دهد.
- {{domxref("HTMLLinkElement.blocking")}}
  - : رشته‌ای که نشان می‌دهد برخی عملیات‌ها باید در هنگام واکشی یک منبع خارجی مسدود شوند. این ویژگی، صفت `blocking` عنصر {{HTMLElement("link")}} را بازتاب می‌دهد.
- {{domxref("HTMLLinkElement.crossOrigin")}}
  - : رشته‌ای که با تنظیمات CORS برای این عنصر لینک مطابقت دارد. برای جزئیات، [ویژگی‌های تنظیمات CORS](/en-US/docs/Web/HTML/Reference/Attributes/crossorigin) را ببینید.
- {{domxref("HTMLLinkElement.disabled")}}
  - : یک مقدار بولی که نشان می‌دهد آیا لینک غیرفعال است یا خیر؛ در حال حاضر فقط برای پیوندهای استایل‌شیت استفاده می‌شود.
- {{domxref("HTMLLinkElement.fetchPriority")}}
  - : یک رشته‌ی اختیاری که نشانه‌ای به مرورگر می‌دهد که چگونه باید واکشیِ یک پیش‌بارگذاری را نسبت به سایر منابع از همان نوع اولویت‌بندی کند. اگر این مقدار ارائه شود، باید یکی از مقادیر مجاز باشد: `high` برای واکشی با اولویت بالاتر، `low` برای واکشی با اولویت پایین‌تر، یا `auto` برای نشان دادن عدم ترجیح (که پیش‌فرض است).
- {{domxref("HTMLLinkElement.href")}}
  - : رشته‌ای که URI منبع هدف را نشان می‌دهد.
- {{domxref("HTMLLinkElement.hreflang")}}
  - : رشته‌ای که کد زبان منبع مرتبط را نشان می‌دهد.
- {{domxref("HTMLLinkElement.imageSizes")}}
  - : رشته‌ای که صفت HTML [`imagesizes`](/en-US/docs/Web/HTML/Reference/Elements/link#imagesizes) را بازتاب می‌دهد؛ فهرستی از شرایط و اندازه‌های تصویر که با ویرگول جدا شده‌اند.
- {{domxref("HTMLLinkElement.imageSrcset")}}
  - : رشته‌ای که صفت HTML [`imagesrcset`](/en-US/docs/Web/HTML/Reference/Elements/link#imagesrcset) را بازتاب می‌دهد؛ فهرستی از رشته‌های کاندیدای تصویر که با ویرگول جدا شده‌اند.
- {{domxref("HTMLLinkElement.integrity")}}
  - : رشته‌ای که فراداده‌ی درون‌خطی را شامل می‌شود که مرورگر می‌تواند از آن برای تأیید اینکه منبع واکشی‌شده بدون دستکاری غیرمنتظره تحویل داده شده است استفاده کند. این ویژگی، صفت `integrity` عنصر {{HTMLElement("link")}} را بازتاب می‌دهد.
- {{domxref("HTMLLinkElement.media")}}
  - : رشته‌ای که فهرستی از یک یا چند قالب رسانه‌ای را نشان می‌دهد که منبع برای آن‌ها اعمال می‌شود. این ویژگی، صفت `media` عنصر {{HTMLElement("link")}} را بازتاب می‌دهد.
- {{domxref("HTMLLinkElement.referrerPolicy")}}
  - : رشته‌ای که صفت HTML [`referrerpolicy`](/en-US/docs/Web/HTML/Reference/Elements/link#referrerpolicy) را بازتاب می‌دهد و نشان می‌دهد کدام مرجع (referrer) استفاده شود.
- {{domxref("HTMLLinkElement.rel")}}
  - : رشته‌ای که رابطه‌ی رو به جلوی منبع مرتبط را از سند به منبع نشان می‌دهد.
- {{domxref("HTMLLinkElement.relList")}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMTokenList")}} که صفت HTML [`rel`](/en-US/docs/Web/HTML/Reference/Elements/link#rel) را به صورت فهرستی از توکن‌ها بازتاب می‌دهد.
- {{domxref("HTMLLinkElement.sizes")}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMTokenList")}} که صفت HTML [`sizes`](/en-US/docs/Web/HTML/Reference/Elements/link#sizes) را به صورت فهرستی از توکن‌ها بازتاب می‌دهد.
- {{domxref("HTMLLinkElement.sheet")}} {{ReadOnlyInline}}
  - : شیء {{domxref("StyleSheet")}} مرتبط با عنصر داده‌شده را بازمی‌گرداند، یا اگر وجود نداشته باشد `null` را برمی‌گرداند.
- {{domxref("HTMLLinkElement.type")}}
  - : رشته‌ای که نوع MIME منبع مرتبط را نشان می‌دهد.

### ویژگی‌های منسوخ

- {{domxref("HTMLLinkElement.charset")}} {{deprecated_inline}}
  - : رشته‌ای که编码 نویسه‌های منبع هدف را نشان می‌دهد.
- {{domxref("HTMLLinkElement.rev")}} {{deprecated_inline}}
  - : رشته‌ای که رابطه‌ی معکوس منبع مرتبط را از منبع به سند نشان می‌دهد.

    > [!NOTE]
    > در حال حاضر مشخصات W3C HTML 5.2 بیان می‌کند که `rev` دیگر منسوخ نیست، در حالی که استاندارد زنده‌ی WHATWG همچنان آن را منسوخ برچسب‌گذاری کرده است. تا زمانی که این اختلاف حل نشود، همچنان باید آن را منسوخ فرض کنید.

- {{domxref("HTMLLinkElement.target")}} {{deprecated_inline}}
  - : رشته‌ای که نام فریم هدفی را نشان می‌دهد که منبع برای آن اعمال می‌شود.

## متدهای نمونه

_متد خاصی ندارد؛ متدها را از والد خود، {{domxref("HTMLElement")}} به ارث می‌برد._

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- عنصر HTML که این رابط را پیاده‌سازی می‌کند: {{HTMLElement("link")}}.
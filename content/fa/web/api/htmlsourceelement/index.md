---
title: HTMLSourceElement
slug: Web/API/HTMLSourceElement
page-type: web-api-interface
browser-compat: api.HTMLSourceElement
---

{{APIRef("HTML DOM")}}

رابط **`HTMLSourceElement`** ویژگی‌های ویژه‌ای (فراتر از رابط شیء معمولی {{domxref("HTMLElement")}} که به‌صورت ارث‌بری نیز در دسترس آن است) را برای کار با عناصر {{htmlelement("source")}} فراهم می‌کند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌های والد خود، {{domxref("HTMLElement")}}، را به ارث می‌برد._

- {{domxref("HTMLSourceElement.height")}}
  - : عددی که ویژگی HTML [`height`](/en-US/docs/Web/HTML/Reference/Elements/source#height) را بازتاب می‌کند و ارتفاع منبع تصویر را بر حسب پیکسل‌های CSS نشان می‌دهد. این ویژگی تنها زمانی معنا دارد که والد عنصر فعلی {{HTMLElement("source")}} یک عنصر {{HTMLElement("picture")}} باشد.
- {{domxref("HTMLSourceElement.media")}}
  - : رشته‌ای که ویژگی HTML [`media`](/en-US/docs/Web/HTML/Reference/Elements/source#media) را بازتاب می‌کند و شامل نوع موردنظر منبع رسانه‌ای است.
- {{domxref("HTMLSourceElement.sizes")}}
  - : رشته‌ای که اندازه‌های تصویر را بین نقاط شکست (breakpoint) نشان می‌دهد.
- {{domxref("HTMLSourceElement.src")}}
  - : رشته‌ای که ویژگی HTML [`src`](/en-US/docs/Web/HTML/Reference/Elements/source#src) را بازتاب می‌کند و شامل URL منبع رسانه‌ای است. ویژگی {{domxref("HTMLSourceElement.src")}} تنها زمانی معنا دارد که عنصر {{HTMLElement("source")}} مرتبط در یک عنصر رسانه‌ای مانند {{htmlelement("video")}} یا {{htmlelement("audio")}} قرار گرفته باشد. اگر این عنصر در یک {{HTMLElement("picture")}} قرار گرفته باشد، این ویژگی هیچ معنایی ندارد و نادیده گرفته می‌شود.

    > [!NOTE]
    > اگر ویژگی `src` (به‌همراه هر عنصر هم‌سطح دیگری) به‌روزرسانی شد، پس از اتمام باید متد `load` والد {{domxref("HTMLMediaElement")}} فراخوانی شود، زیرا عناصر `<source>` به‌صورت خودکار دوباره پویش نمی‌شوند.

- {{domxref("HTMLSourceElement.srcset")}}
  - : رشته‌ای که ویژگی HTML [`srcset`](/en-US/docs/Web/HTML/Reference/Elements/source#srcset) را بازتاب می‌کند و شامل فهرستی از تصاویر نامزد است که با یک کاما (`',', U+002C COMMA`) از هم جدا شده‌اند. یک تصویر نامزد، یک URL و سپس یک `'w'` به‌همراه عرض تصاویر، یا یک `'x'` به‌همراه تراکم پیکسلی است.
- {{domxref("HTMLSourceElement.type")}}
  - : رشته‌ای که ویژگی HTML [`type`](/en-US/docs/Web/HTML/Reference/Elements/source#type) را بازتاب می‌کند و شامل نوع منبع رسانه‌ای است.
- {{domxref("HTMLSourceElement.width")}}
  - : عددی که ویژگی HTML [`width`](/en-US/docs/Web/HTML/Reference/Elements/source#width) را بازتاب می‌کند و عرض منبع تصویر را بر حسب پیکسل‌های CSS نشان می‌دهد. این ویژگی تنها زمانی معنا دارد که والد عنصر فعلی {{HTMLElement("source")}} یک عنصر {{HTMLElement("picture")}} باشد.

## متدهای نمونه

_هیچ متد خاصی ندارد؛ متدهای والد خود، {{domxref("HTMLElement")}}، را به ارث می‌برد._

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- عنصر HTML که این رابط را پیاده‌سازی می‌کند: {{ HTMLElement("source") }}.
- رابط‌های DOM عناصر HTML که می‌توانند حاوی یک عنصر {{HTMLElement("source")}} باشند: {{domxref("HTMLVideoElement")}}، {{domxref("HTMLAudioElement")}}، {{domxref("HTMLPictureElement")}}.
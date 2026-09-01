---
title: HTMLEmbedElement
slug: Web/API/HTMLEmbedElement
page-type: web-api-interface
browser-compat: api.HTMLEmbedElement
---

{{APIRef("HTML DOM")}}

اینترفیس **`HTMLEmbedElement`** ویژگی‌های خاصی (فراتر از اینترفیس معمول {{domxref("HTMLElement")}} که به‌صورت ارث‌بری نیز در دسترس آن است) برای کار با عناصر {{HTMLElement("embed")}} فراهم می‌کند.

> [!NOTE]
> این موضوع، اینترفیس `HTMLEmbedElement` را طبق استاندارد توصیف می‌کند و به نسخه‌های قدیمی‌تر و غیراستاندارد این اینترفیس نمی‌پردازد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌های والد خود، {{domxref("HTMLElement")}} را به ارث می‌برد._

- {{domxref("HTMLEmbedElement.align")}} {{deprecated_inline}}
  - : رشته‌ای که یک ویژگی شمارشی را نشان می‌دهد و تراز محتوای عنصر را نسبت به زمینه اطراف مشخص می‌کند. مقادیر ممکن عبارتند از `"left"`، `"right"`، `"center"` و `"justify"`.
- {{domxref("HTMLEmbedElement.height")}}
  - : رشته‌ای که ویژگی HTML [`height`](/en-US/docs/Web/HTML/Reference/Elements/embed#height) را منعکس می‌کند و ارتفاع نمایش داده‌شده منبع را شامل می‌شود.
- {{domxref("HTMLEmbedElement.name")}} {{deprecated_inline}}
  - : رشته‌ای که نام شیء تعبیه‌شده را نشان می‌دهد.
- {{domxref("HTMLEmbedElement.src")}}
  - : رشته‌ای که ویژگی HTML [`src`](/en-US/docs/Web/HTML/Reference/Elements/embed#src) را منعکس می‌کند و آدرس منبع را شامل می‌شود.
- {{domxref("HTMLEmbedElement.type")}}
  - : رشته‌ای که ویژگی HTML [`type`](/en-US/docs/Web/HTML/Reference/Elements/embed#type) را منعکس می‌کند و نوع منبع را شامل می‌شود.
- {{domxref("HTMLEmbedElement.width")}}
  - : رشته‌ای که ویژگی HTML [`width`](/en-US/docs/Web/HTML/Reference/Elements/embed#width) را منعکس می‌کند و عرض نمایش داده‌شده منبع را شامل می‌شود.

## روش‌های نمونه

_همچنین روش‌های اینترفیس والد خود، {{domxref("HTMLElement")}} را به ارث می‌برد._

- {{domxref("HTMLEmbedElement.getSVGDocument()")}}
  - : SVG تعبیه‌شده را به‌صورت یک {{domxref("Document")}} برمی‌گرداند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- عنصر HTML که این اینترفیس را پیاده‌سازی می‌کند: {{ HTMLElement("embed") }}

---
title: "HTMLOListElement"
---

{{ APIRef("HTML DOM") }}

رابط **`HTMLOListElement`** ویژگی‌های خاصی (علاوه بر ویژگی‌های تعریف‌شده در رابط {{domxref("HTMLElement")}} که به صورت ارث‌بری در دسترس است) برای کار با عناصر لیست مرتب‌شده فراهم می‌کند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌های رابط والد خود، {{domxref("HTMLElement")}} را به ارث می‌برد._

- {{domxref("HTMLOListElement.reversed")}}
  - : یک مقدار بولی که منعکس‌کننده ویژگی [`reversed`](/en-US/docs/Web/HTML/Reference/Elements/ol#reversed) است و مشخص می‌کند که شماره‌گذاری نزولی است (یعنی مقدار آن `true` است) یا صعودی (`false`).
- {{domxref("HTMLOListElement.start")}}
  - : یک مقدار از نوع `long` که منعکس‌کننده ویژگی [`start`](/en-US/docs/Web/HTML/Reference/Elements/ol#start) است و مقدار اولین عدد از اولین عنصر لیست را مشخص می‌کند.
- {{domxref("HTMLOListElement.type")}}
  - : یک مقدار رشته‌ای که منعکس‌کننده ویژگی [`type`](/en-US/docs/Web/HTML/Reference/Elements/ol#type) است و نوع نشانگر مورد استفاده برای نمایش را تعیین می‌کند. می‌تواند مقادیر زیر را داشته باشد:
    - `'1'` به این معنی که از اعداد اعشاری استفاده می‌شود: `1`، `2`، `3`، `4`، `5`، …
    - `'a'` به این معنی که از الفبای لاتین کوچک استفاده می‌شود: `a`، `b`، `c`، `d`، `e`، …
    - `'A'` به این معنی که از الفبای لاتین بزرگ استفاده می‌شود: `A`، `B`، `C`، `D`، `E`، …
    - `'i'` به این معنی که از اعداد لاتین کوچک استفاده می‌شود: `i`، `ii`، `iii`، `iv`، `v`، …
    - `'I'` به این معنی که از اعداد لاتین بزرگ استفاده می‌شود: `I`، `II`، `III`، `IV`، `V`، …

- {{domxref("HTMLOListElement.compact")}} {{deprecated_inline}}
  - : یک مقدار بولی که نشان می‌دهد فاصله بین آیتم‌های لیست باید کاهش یابد. این ویژگی فقط منعکس‌کننده صفت [`compact`](/en-US/docs/Web/HTML/Reference/Elements/ol#compact) است و ویژگی CSS {{cssxref("line-height")}} که در صفحات مدرن برای این رفتار استفاده می‌شود را در نظر نمی‌گیرد.

## روش‌های نمونه

_هیچ متد خاصی ندارد؛ متدهای خود را از والد خود، {{domxref("HTMLElement")}} به ارث می‌برد._

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- عنصر HTML که این رابط را پیاده‌سازی می‌کند: {{ HTMLElement("ol") }}.
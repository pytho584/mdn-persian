---
title: HTMLLIElement
slug: Web/API/HTMLLIElement
page-type: web-api-interface
browser-compat: api.HTMLLIElement
---

{{ APIRef("HTML DOM") }}

رابطِ **`HTMLLIElement`** ویژگی‌ها و روش‌های خاصی را برای کار با المان‌های فهرست در دسترس قرار می‌دهد (علاوه بر آن‌هایی که از رابط معمول {{domxref("HTMLElement")}} به ارث برده است).

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌های والد خود، {{domxref("HTMLElement")}} را به ارث می‌برد._

- {{domxref("HTMLLIElement.type")}} {{deprecated_inline}}
  - : رشته‌ای که نوع نشانگر (bullet) را مشخص می‌کند: `"disc"`، `"square"` یا `"circle"`. از آنجا که روش استاندارد برای تعیین نوع فهرست، استفاده از ویژگی CSS {{cssxref("list-style-type")}} است، برای تنظیم آن با اسکریپت باید از متدهای CSSOM استفاده کنید.
- {{domxref("HTMLLIElement.value")}}
  - : یک عدد صحیح که موقعیت ترتیبیِ _المان فهرست_ را در یک {{HTMLElement("ol")}} نشان می‌دهد. این ویژگی، منعکس‌کنندهٔ ویژگی `value` المان HTML {{HTMLElement("li")}} است و می‌تواند کمتر از `0` باشد. اگر المان {{HTMLElement("li")}} فرزند یک المان {{HTMLElement("ol")}} نباشد، این ویژگی معنایی ندارد.

## روش‌های نمونه

_روش خاصی وجود ندارد؛ روش‌های والد خود، {{domxref("HTMLElement")}} را به ارث می‌برد._

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- المان HTML که این رابط را پیاده‌سازی می‌کند: {{HTMLElement("li")}}
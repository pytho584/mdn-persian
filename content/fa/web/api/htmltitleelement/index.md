---
title: HTMLTitleElement
slug: Web/API/HTMLTitleElement
page-type: web-api-interface
browser-compat: api.HTMLTitleElement
---

{{ APIRef("HTML DOM") }}

رابط **`HTMLTitleElement`** توسط عنصر {{ HTMLElement( "title" )}} یک سند پیاده‌سازی می‌شود. این عنصر تمام ویژگی‌ها و روش‌های رابط {{domxref("HTMLElement")}} را به ارث می‌برد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌های والد خود، {{domxref("HTMLElement")}} را به ارث می‌برد._

- {{domxref("HTMLTitleElement.text")}}
  - : یک رشته که متن عنوان سند را نشان می‌دهد.

## روش‌های نمونه

_روش خاصی ندارد؛ روش‌های والد خود، {{domxref("HTMLElement")}} را به ارث می‌برد._

## مثال

اشتباه نگیرید: `document.title` با `document.querySelector('title')`

اولی صرفاً یک متد setter/getter برای تنظیم یا دریافت مقدار متن داخلی عنوان سند است، در حالی که دومی شیء `HTMLTitleElement` است. بنابراین نمی‌توانید بنویسید: `document.title.text = "Hello world!";`

در عوض، می‌توانید به سادگی بنویسید: `document.title = "Hello world!";` که معادل `document.querySelector('title').text = "Hello world!";` است.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- عنصر HTML که این رابط را پیاده‌سازی می‌کند: {{ HTMLElement("title") }}.
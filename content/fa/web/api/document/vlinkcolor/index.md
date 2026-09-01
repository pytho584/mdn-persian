---
title: "Document: vlinkColor property"
short-title: vlinkColor
slug: Web/API/Document/vlinkColor
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.Document.vlinkColor
---

{{APIRef("DOM")}} {{Deprecated_Header}}

خاصیت **`Document.vlinkColor`** رنگ پیوندهایی را که کاربر در سند بازدید کرده است، دریافت یا تعیین می‌کند.

## مقدار

یک رشته که رنگ را به صورت یک کلمه (مانند `"red"`) یا مقدار هگزادسیمال (مانند `"#ff0000"`) نشان می‌دهد.

وقتی مقدار `null` تنظیم شود، آن مقدار `null` به رشته خالی (`""`) تبدیل می‌شود، بنابراین `document.vlinkColor = null` معادل `document.vlinkColor = ""` است.

## نکات

- مقدار پیش‌فرض این خاصیت در Mozilla Firefox بنفش است (`#551a8b` در هگزادسیمال).
- `Document.vlinkColor` در [مشخصات HTML](https://html.spec.whatwg.org/multipage/obsolete.html#dom-document-vlinkcolor) منسوخ شده است.
- جایگزین پیشنهادی، دریافت/تنظیم رنگ شبه‌کلاس CSS {{Cssxref(":visited")}} بر روی عناصر HTML {{HtmlElement("a")}} است (مثلاً `a:visited {color:red;}`).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
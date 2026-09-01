---
title: "Document: alinkColor property"
short-title: alinkColor
slug: Web/API/Document/alinkColor
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.Document.alinkColor
---

{{APIRef("DOM")}}{{Deprecated_header}}

رنگ یک پیوند فعال در بدنه سند را برمی‌گرداند یا تنظیم می‌کند. یک پیوند در فاصله زمانی بین رویدادهای `mousedown` و `mouseup` فعال است.

## مقدار

یک رشته شامل نام رنگ (مانند `blue`، `darkblue` و غیره) یا مقدار هگزادسیمال رنگ (مانند `#0000FF`).

وقتی روی مقدار `null` تنظیم شود، آن مقدار `null` به رشته خالی (`""`) تبدیل می‌شود، بنابراین `document.alinkColor = null` معادل `document.alinkColor = ""` است.

## نکات

مقدار پیش‌فرض این ویژگی در Mozilla Firefox قرمز است (در هگزادسیمال `#ee0000`).

`document.alinkColor` در [مشخصات HTML](https://html.spec.whatwg.org/multipage/obsolete.html#dom-document-alinkcolor) منسوخ شده است. یک جایگزین، انتخابگر CSS {{Cssxref(":active")}} است.

Firefox هر دو `alinkColor`/`:active` و {{Cssxref(":focus")}} را پشتیبانی می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
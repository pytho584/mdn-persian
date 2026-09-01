---
title: "Document: linkColor property"
short-title: linkColor
slug: Web/API/Document/linkColor
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.Document.linkColor
---

{{APIRef("DOM")}} {{Deprecated_header}}

**ویژگی `Document.linkColor`** رنگِ پیوندهای داخل سند را می‌خواند یا تنظیم می‌کند.

این ویژگی منسوخ شده است. به‌عنوان جایگزین، می‌توانید ویژگی CSS {{cssxref("color")}} را روی پیوندهای لنگر HTML ({{HtmlElement("a")}}) یا روی شبه‌کلاس‌های {{cssxref(":link")}} تنظیم کنید.

## مقدار

یک رشته که رنگ را به‌صورت یک واژه (مثلاً `red`) یا یک مقدار هگزادسیمال (مثلاً `#ff0000`) نشان می‌دهد.

وقتی روی مقدار `null` تنظیم شود، آن مقدار `null` به رشتهٔ خالی (`""`) تبدیل می‌شود؛ بنابراین `document.linkColor = null` معادل `document.linkColor = ""` است.

## مثال‌ها

```js
document.linkColor = "blue";
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

مقدار پیش‌فرض این ویژگی در Mozilla Firefox آبی (`#0000ee` در هگزادسیمال) است.

## جستارهای وابسته

- {{domxref("document.vlinkColor")}}
- {{domxref("document.alinkColor")}}
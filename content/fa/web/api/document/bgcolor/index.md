---
title: "Document: bgColor property"
short-title: bgColor
slug: Web/API/Document/bgColor
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.Document.bgColor
---

{{APIRef("DOM")}} {{Deprecated_Header}}

ویژگی منسوخ‌شدهٔ `bgColor`، رنگ پس‌زمینهٔ سند جاری را دریافت یا تنظیم می‌کند.

## مقدار

یک رشته که رنگ را به‌صورت یک کلمه (مثلاً `"red"`) یا یک مقدار هگزادسیمال (مثلاً `"#ff0000"`) نمایش می‌دهد.

وقتی این ویژگی روی مقدار `null` تنظیم شود، آن مقدار به رشتهٔ خالی (`""`) تبدیل می‌شود؛ بنابراین `document.bgColor = null` معادل `document.bgColor = ""` است.

## مثال‌ها

```js
document.bgColor = "darkblue";
```

## نکات

مقدار پیش‌فرض این ویژگی در فایرفاکس سفید است (در نمایش هگزادسیمال `#ffffff`).

`document.bgColor` در [مشخصات HTML](https://html.spec.whatwg.org/multipage/obsolete.html#dom-document-bgcolor) منسوخ اعلام شده است. جایگزین پیشنهادی استفاده از استایل CSS، یعنی {{Cssxref("background-color")}} است که از طریق DOM با `document.body.style.backgroundColor` قابل دسترسی است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
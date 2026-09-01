---
title: "HTMLFormElement: acceptCharset property"
short-title: acceptCharset
slug: Web/API/HTMLFormElement/acceptCharset
page-type: web-api-instance-property
browser-compat: api.HTMLFormElement.acceptCharset
---

{{APIRef("HTML DOM")}}

ویژگی **`HTMLFormElement.acceptCharset`** نشان‌دهندهٔ {{glossary("character encoding","رمزگذاری نویسه‌ها")}} برای عنصر {{htmlelement("form")}} داده شده است.

این مشخصات تنها یک مقدار بدون حساسیت به بزرگی/کوچکی حروف به نام `"UTF-8"` را مجاز می‌داند که نشان‌دهندهٔ فراگیری این رمزگذاری است (از نظر تاریخی، چندین رمزگذاری نویسه می‌توانستند به صورت فهرست جدا شده با کاما یا فاصله مشخص شوند).

این ویژگی منعکس‌کنندهٔ مقدار ویژگی HTML [`accept-charset`](/en-US/docs/Web/HTML/Reference/Elements/form#accept-charset) فرم است.

## مقدار

یک رشته که می‌تواند یک تطابق بدون حساسیت به بزرگی/کوچکی حروف با `UTF-8` باشد.

## مثال‌ها

```js
let charSet = document.forms["my-form"].acceptCharset;
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}
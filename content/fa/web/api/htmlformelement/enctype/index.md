---
title: "HTMLFormElement: enctype property"
short-title: enctype
slug: Web/API/HTMLFormElement/enctype
page-type: web-api-instance-property
browser-compat: api.HTMLFormElement.enctype
---

{{APIRef("HTML DOM")}}

ویژگی **`HTMLFormElement.enctype`**، نوع {{Glossary("MIME_type", "MIME")}} محتوایی است که برای ارسال فرم به سرور استفاده می‌شود. مقادیر ممکن عبارتند از:

- `application/x-www-form-urlencoded`: نوع پیش‌فرض اولیه.
- `multipart/form-data`: نوعی که به عنصر(های) {{HTMLElement("input")}} اجازه می‌دهد داده فایل را بارگذاری کنند.
- `text/plain`: قالب مبهم؛ محتوای قابل خواندن برای انسان که توسط رایانه به‌طور قابل اطمینان تفسیر نمی‌شود.

این مقدار می‌تواند توسط ویژگی [`formenctype`](/en-US/docs/Web/HTML/Reference/Elements/button#formenctype) روی یک عنصر {{HTMLElement("button")}} یا {{HTMLElement("input")}} بازنویسی شود.

## مقدار

یک رشته.

## مثال‌ها

```js
form.enctype = "application/x-www-form-urlencoded";
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
---
title: "HTMLFormElement: rel property"
short-title: rel
slug: Web/API/HTMLFormElement/rel
page-type: web-api-instance-property
browser-compat: api.HTMLFormElement.rel
---

{{APIRef("HTML DOM")}}

ویژگی **`rel`** در رابط {{domxref("HTMLFormElement")}} بازتابدهندهٔ ویژگی [`rel`](/en-US/docs/Web/HTML/Reference/Attributes/rel) است. این ویژگی یک رشته است که مشخص می‌کند عنصر HTML {{HTMLElement("form")}} چه نوع پیوندهایی ایجاد می‌کند، به‌صورت فهرستی از مقادیر شمارشی که با فاصله از هم جدا شده‌اند.

برای دریافت مقدار به‌صورت آرایه‌ای از نشانه‌ها (tokens)، از {{domxref("HTMLFormElement.relList")}} استفاده کنید.

## مقدار

یک رشته.

## مثال‌ها

```js
const form = document.querySelector("form");
console.log(form.rel);

form.rel = "noopener noreferrer";
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLFormElement.relList")}}
- {{domxref("HTMLLinkElement.rel")}}
- {{domxref("HTMLAnchorElement.rel")}}
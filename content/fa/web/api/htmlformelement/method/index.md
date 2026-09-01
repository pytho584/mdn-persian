---
title: "HTMLFormElement: method property"
short-title: method
slug: Web/API/HTMLFormElement/method
page-type: web-api-instance-property
browser-compat: api.HTMLFormElement.method
---

{{APIRef("HTML DOM")}}

ویژگی **`HTMLFormElement.method`** نشان‌دهندهٔ متد {{Glossary("HTTP")}} مورد استفاده برای ارسال {{HtmlElement("form")}} است.

اگر به طور صریح مشخص نشده باشد، متد پیش‌فرض 'get' است.

## مقدار

یک رشته (string).

## مثال‌ها

```js
document.forms["my-form"].method = "post";

const formElement = document.createElement("form"); // ایجاد یک فرم
document.body.appendChild(formElement);
console.log(formElement.method); // 'get'
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}
---
title: "HTMLFormElement: name property"
short-title: name
slug: Web/API/HTMLFormElement/name
page-type: web-api-instance-property
browser-compat: api.HTMLFormElement.name
---

{{APIRef("HTML DOM")}}

ویژگی **`HTMLFormElement.name`** نمایانگر نام عنصر {{HtmlElement("form")}} جاری به صورت یک رشته است.

اگر عنصر {{HTMLElement("Form")}} شما شامل عنصری با نام _name_ باشد، آن عنصر ویژگی `form.name` را بازنویسی می‌کند و بنابراین نمی‌توانید به آن دسترسی داشته باشید.

## مقدار

یک رشته.

## مثال‌ها

```js
const form1name = document.getElementById("form1").name;

if (form1name !== document.form.form1) {
  // Browser doesn't support this form of reference
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}
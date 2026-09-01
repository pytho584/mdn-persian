---
title: "Document: getElementsByName() method"
short-title: getElementsByName()
slug: Web/API/Document/getElementsByName
page-type: web-api-instance-method
browser-compat: api.Document.getElementsByName
---

{{APIRef("DOM")}}

متد **`getElementsByName()`** از شیء {{domxref("Document")}} یک مجموعه {{domxref("NodeList")}} از عناصری را برمی‌گرداند که دارای ویژگی `name` مشخصی در سند هستند.

## نحو (Syntax)

```js-nolint
getElementsByName(name)
```

### پارامترها

- `name`
  - : مقدار ویژگی `name` عنصر(هایی) که به دنبال آن هستیم.

### مقدار بازگشتی

یک مجموعه زنده (live) از نوع {{domxref("NodeList")}}، به این معنی که به‌طور خودکار به‌روزرسانی می‌شود زمانی که عناصر جدید با همان `name` به سند اضافه یا از آن حذف می‌شوند.

## مثال‌ها

```html
<!doctype html>
<html lang="en">
  <head>
    <title>Example: using document.getElementsByName</title>
  </head>
  <body>
    <input type="hidden" name="up" />
    <input type="hidden" name="down" />
  </body>
</html>
```

```js
const upNames = document.getElementsByName("up");
console.log(upNames[0].tagName); // displays "INPUT"
```

## نکات

ویژگی `name` فقط در اسناد (X)HTML قابل استفاده است.

مجموعه {{domxref("NodeList")}} بازگشتی شامل _همه_ عناصر با `name` داده شده است، مانند {{htmlelement("meta")}}، {{htmlelement("object")}} و حتی عناصری که اصلاً از ویژگی `name` پشتیبانی نمی‌کنند.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("document.getElementById()")}} برای بازگرداندن ارجاع به یک عنصر با `id` منحصربه‌فرد آن
- {{domxref("document.getElementsByTagName()")}} برای بازگرداندن ارجاع به عناصر با [نام تگ](/en-US/docs/Web/API/Element/tagName) یکسان
- {{domxref("document.querySelector()")}} برای بازگرداندن ارجاع به عناصر با استفاده از انتخاب‌گرهای CSS مانند `'div.myclass'`
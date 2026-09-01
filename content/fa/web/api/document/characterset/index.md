---
title: "Document: characterSet property"
short-title: characterSet
slug: Web/API/Document/characterSet
page-type: web-api-instance-property
browser-compat: api.Document.characterSet
---

{{ ApiRef("DOM") }}

ویژگی فقط‌خواندنی **`Document.characterSet`**، [رمزگذاری نویسه‌ها](/en-US/docs/Glossary/Character_encoding) سندی را که در حال حاضر با آن رندر می‌شود، برمی‌گرداند.

> [!NOTE]
> «مجموعه نویسه‌ها» (character set) و «رمزگذاری نویسه‌ها» (character encoding) مفاهیمی مرتبط اما متفاوت هستند. با وجود نام این ویژگی، مقدار بازگشتی آن _رمزگذاری_ است.

## مقدار

یک رشته (string).

## مثال‌ها

```js
console.log(document.characterSet);
// رمزگذاری نویسه‌های سند، مانند "ISO-8859-1" یا "UTF-8"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}
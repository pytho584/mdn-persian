---
title: "HTMLElement: lang property"
---

---
title: "HTMLElement: lang property"
short-title: lang
slug: Web/API/HTMLElement/lang
page-type: web-api-instance-property
browser-compat: api.HTMLElement.lang
---

{{ APIRef("HTML DOM") }}

خاصیت **`lang`** در رابط {{domxref("HTMLElement")}} زبان پایهٔ مقادیر ویژگی‌ها و محتوای متنی یک عنصر را به شکل یک {{glossary("BCP 47 language tag")}} (برچسب زبان BCP 47) مشخص می‌کند. این خاصیت، ویژگی [`lang`](/en-US/docs/Web/HTML/Reference/Global_attributes/lang) عنصر را بازتاب می‌دهد؛ ویژگی `xml:lang` تأثیری بر این خاصیت ندارد.

توجه داشته باشید که اگر ویژگی `lang` مشخص نشده باشد، خود عنصر ممکن است همچنان زبان را از والد خود به ارث ببرد؛ با این حال، این زبانِ به‌ارث‌برده در مقدار این خاصیت منعکس نمی‌شود.

## مقدار

یک رشته است. مثال‌های رایج عبارت‌اند از `"en"` برای انگلیسی، `"ja"` برای ژاپنی، `"es"` برای اسپانیایی و غیره. اگر ویژگی `lang` تعیین نشده باشد، مقدار این خاصیت یک رشتهٔ خالی است.

## مثال‌ها

```js
// this snippet compares the base language and
// redirects to another URL based on language
if (document.documentElement.lang === "en") {
  window.location.href = "Some_document.html.en";
} else if (document.documentElement.lang === "ru") {
  window.location.href = "Some_document.html.ru";
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}
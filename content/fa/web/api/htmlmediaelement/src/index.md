---
title: "HTMLMediaElement: src property"
---

---
title: "HTMLMediaElement: src property"
short-title: src
slug: Web/API/HTMLMediaElement/src
page-type: web-api-instance-property
browser-compat: api.HTMLMediaElement.src
---

{{APIRef("HTML DOM")}}

ویژگی **`HTMLMediaElement.src`** مقدارِ صفت (attribute) `src` عنصر رسانهٔ HTML را بازتاب می‌دهد؛ این صفت، URL منبع رسانه‌ای را که باید در عنصر استفاده شود مشخص می‌کند.

> [!NOTE]
> بهترین راه برای دانستن URL منبع رسانه‌ای که در حال حاضر در این عنصر استفاده می‌شود، نگاه کردن به مقدارِ ویژگی {{domxref("HTMLMediaElement.currentSrc", "currentSrc")}} است؛ این ویژگی، انتخاب بهترین یا ترجیحی‌ترین منبع رسانه از فهرستی را که در یک {{domxref("HTMLSourceElement")}} (که نمایانگر عنصر {{HTMLElement("source")}} است) ارائه شده، نیز در نظر می‌گیرد.

## مقدار

یک رشته (string) شامل URL منبع رسانه‌ای برای استفاده در عنصر؛ این ویژگی مقدارِ صفت `src` عنصر HTML را بازتاب می‌دهد.

## مثال‌ها

```js
const obj = document.createElement("video");
console.log(obj.src); // ""
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLMediaElement")}}: اینترفیسی که برای تعریف ویژگی `HTMLMediaElement.src` استفاده می‌شود.
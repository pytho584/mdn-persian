---
title: "Document: children property"
short-title: children
slug: Web/API/Document/children
page-type: web-api-instance-property
browser-compat: api.Document.children
---

{{ APIRef("DOM") }}

خاصیت فقط‌خواندنی **`children`** یک {{domxref("HTMLCollection")}} زنده برمی‌گرداند که شامل تمام عناصر فرزند ({{domxref("Element", "elements")}}) سندی است که روی آن فراخوانی شده است.

برای اسناد HTML، این معمولاً فقط عنصر ریشه `<html>` است.

برای عناصر فرزند المان‌های HTML خاص درون سند، به {{domxref("Element.children")}} مراجعه کنید.

## مقدار

یک {{ domxref("HTMLCollection") }} که یک مجموعه زنده و مرتب از المان‌های DOM است که فرزندان سند جاری هستند. می‌توانید به گره‌های فرزند جداگانه در مجموعه دسترسی داشته باشید یا با استفاده از متد {{domxref("HTMLCollection.item()", "item()")}} روی مجموعه، یا با استفاده از نماد آرایه‌ای جاوااسکریپت.

اگر سند هیچ عنصر فرزندی نداشته باشد، `children` یک لیست خالی با `length` برابر `0` است.

## مثال‌ها

```js
document.children;
// HTMLCollection [<html>]
// Usually only contains the root <html> element, the document's only direct child
```

برای عناصر فرزند المان‌های HTML خاص درون سند، به {{domxref("Element.children")}} مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.children")}}
- {{domxref("Node.childNodes")}}
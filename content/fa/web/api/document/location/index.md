---
title: "Document: location property"
short-title: location
slug: Web/API/Document/location
page-type: web-api-instance-property
browser-compat: api.Document.location
---

{{APIRef("DOM")}}

ویژگی فقط-خواندنی **`location`** در واسط {{domxref("Document")}} یک شیء {{domxref("Location")}} برمی‌گرداند که اطلاعاتی دربارهٔ URL سند دارد و روش‌هایی برای تغییر آن URL و بارگذاری URL دیگر ارائه می‌دهد.

برای دریافت تنها URL به‌صورت یک رشته، می‌توان از ویژگی فقط-خواندنی {{domxref("document.URL")}} نیز استفاده کرد.

## مقدار

یک شیء {{domxref("Location")}}. اگر سند جاری در یک بافت مرور (browsing context) نباشد، مقدار برگشتی `null` خواهد بود.

اگرچه خود ویژگی `location` از این نظر که نمی‌توانید شیء `Location` را جایگزین کنید فقط-خواندنی است، اما همچنان می‌توانید مستقیماً به ویژگی `location` مقداردهی کنید که معادل مقداردهی به ویژگی {{domxref("Location/href", "href")}} آن است. همچنین می‌توانید شیء `Location` را با استفاده از روش‌های {{domxref("Location/assign", "assign()")}} و {{domxref("Location/replace", "replace()")}} تغییر دهید.

## مثال‌ها

```js
console.log(document.location);
// یک شیء Location را در کنسول چاپ می‌کند
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- واسط مقدار برگشتی، {{domxref("Location")}}
- اطلاعات مشابه، اما متصل به {{Glossary("browsing context", "بافت مرور")}}، {{domxref("Window.location")}}
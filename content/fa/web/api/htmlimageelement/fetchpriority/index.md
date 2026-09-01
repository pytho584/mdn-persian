---
title: "HTMLImageElement: fetchPriority property"
short-title: fetchPriority
slug: Web/API/HTMLImageElement/fetchPriority
page-type: web-api-instance-property
browser-compat: api.HTMLImageElement.fetchPriority
---

{{APIRef("HTML DOM")}}

ویژگی **`fetchPriority`** از رابط {{domxref("HTMLImageElement")}} یک راهنمایی برای مرورگر است که نشان می‌دهد چگونه باید اولویت بارگیری یک تصویر خاص را نسبت به تصاویر دیگر تعیین کند. این ویژگی منعکس‌کنندهٔ ویژگی محتوایی [`fetchpriority`](/en-US/docs/Web/HTML/Reference/Elements/img#fetchpriority) عنصر `<img>` است.

## مقدار

یک رشته که مقدار آن یکی از `high`، `low` یا `auto` است. برای معانی آن‌ها، به ویژگی HTML [`fetchpriority`](/en-US/docs/Web/HTML/Reference/Attributes/fetchpriority) مراجعه کنید.

## مثال‌ها

```js
const img = new Image();
img.fetchPriority = "high";
img.src = "img/logo.png";
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLLinkElement.fetchPriority")}}
- {{domxref("HTMLScriptElement.fetchPriority")}}
- هدر HTTP {{httpheader("Link")}}
- برای اطلاعات دربارهٔ چگونگی تأثیر این API بر اولویت‌ها در Chrome، مطلب [بهینه‌سازی بارگیری منابع با Fetch Priority API](https://web.dev/articles/fetch-priority?hl=en#browser_priority_and_fetchpriority) را مطالعه کنید.
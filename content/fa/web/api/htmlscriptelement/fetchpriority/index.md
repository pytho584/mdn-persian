---
title: "HTMLScriptElement: fetchPriority property"
short-title: fetchPriority
slug: Web/API/HTMLScriptElement/fetchPriority
page-type: web-api-instance-property
browser-compat: api.HTMLScriptElement.fetchPriority
---

{{APIRef("HTML DOM")}}

ویژگی **`fetchPriority`** از رابط {{domxref("HTMLScriptElement")}} یک راهنمایی به مرورگر است که نشان می‌دهد چگونه اولویت بارگیری یک اسکریپت خارجی را نسبت به سایر اسکریپت‌های خارجی تعیین کند. این ویژگی، ویژگی محتوایی [`fetchpriority`](/en-US/docs/Web/HTML/Reference/Elements/script#fetchpriority) عنصر `<script>` را منعکس می‌کند.

## مقدار

یک رشته. برای مقادیر مجاز، به ویژگی HTML [`fetchpriority`](/en-US/docs/Web/HTML/Reference/Attributes/fetchpriority) مراجعه کنید.

## مثال‌ها

```html
<script id="el" type="module" src="main.js" fetchpriority="high"></script>
```

```js
const el = document.getElementById("el");
console.log(el.fetchPriority); // خروجی: "high"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLImageElement.fetchPriority")}}
- {{domxref("HTMLLinkElement.fetchPriority")}}
- هدر HTTP {{httpheader("Link")}}
- [بهینه‌سازی بارگیری منابع با Fetch Priority API](https://web.dev/articles/fetch-priority?hl=en#browser_priority_and_fetchpriority) برای اطلاعات درباره نحوه تأثیر این API بر اولویت‌ها در Chrome.
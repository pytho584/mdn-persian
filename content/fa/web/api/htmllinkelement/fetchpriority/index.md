---
title: "HTMLLinkElement: fetchPriority property"
short-title: fetchPriority
slug: Web/API/HTMLLinkElement/fetchPriority
page-type: web-api-instance-property
browser-compat: api.HTMLLinkElement.fetchPriority
---

{{APIRef("HTML DOM")}}

ویژگی **`fetchPriority`** در رابط {{domxref("HTMLLinkElement")}} راهنمایی به مرورگر است که نشان می‌دهد چگونه باید واکشی یک منبع مشخص را نسبت به سایر منابع از همان نوع اولویت‌بندی کند. این ویژگی، ویژگی محتوایی [`fetchpriority`](/en-US/docs/Web/HTML/Reference/Elements/link#fetchpriority) عنصر `<link>` را منعکس می‌کند.

## مقدار

یک رشته (string). برای مقادیر مجاز، به ویژگی [`fetchpriority`](/en-US/docs/Web/HTML/Reference/Attributes/fetchpriority) در HTML مراجعه کنید.

## مثال‌ها

```js
const preloadLink = document.createElement("link");
preloadLink.href = "my-image.jpg";
preloadLink.rel = "preload";
preloadLink.as = "image";
preloadLink.fetchPriority = "high";
document.head.appendChild(preloadLink);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("HTMLImageElement.fetchPriority")}}
- {{domxref("HTMLScriptElement.fetchPriority")}}
- هدر HTTP {{httpheader("Link")}}
- برای اطلاعات درباره این‌که این API چگونه اولویت‌ها را در Chrome تحت تأثیر قرار می‌دهد، به [Optimize resource loading with the Fetch Priority API](https://web.dev/articles/fetch-priority?hl=en#browser_priority_and_fetchpriority) مراجعه کنید.
---
title: "HTMLScriptElement: defer property"
short-title: defer
slug: Web/API/HTMLScriptElement/defer
page-type: web-api-instance-property
browser-compat: api.HTMLScriptElement.defer
---

{{APIRef("HTML DOM")}}

ویژگی **`defer`** در رابط {{domxref("HTMLScriptElement")}} یک مقدار بولی است که نحوه اجرای اسکریپت را کنترل می‌کند. برای اسکریپت‌های کلاسیک، اگر ویژگی `defer` روی `true` تنظیم شود، اسکریپت خارجی پس از تجزیه (parse) سند اجرا می‌شود، اما قبل از رویداد {{domxref("Document/DOMContentLoaded_event", "DOMContentLoaded")}}. برای [اسکریپت‌های ماژول](/en-US/docs/Web/JavaScript/Guide/Modules)، ویژگی `defer` هیچ اثری ندارد.

این ویژگی منعکس‌کننده ویژگی `defer` عنصر {{HTMLElement("script")}} است.

## مقدار

یک مقدار بولی.

## مثال‌ها

```html
<script id="el" src="/example.js" defer></script>
```

```js
const el = document.getElementById("el");
console.log(el.defer); // Output: true
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("HTMLScriptElement.async")}}
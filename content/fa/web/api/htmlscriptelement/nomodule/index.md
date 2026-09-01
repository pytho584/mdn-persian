---
title: "HTMLScriptElement: noModule property"
short-title: noModule
slug: Web/API/HTMLScriptElement/noModule
page-type: web-api-instance-property
browser-compat: api.HTMLScriptElement.noModule
---

{{APIRef("HTML DOM")}}

ویژگی **`noModule`** در رابط {{domxref("HTMLScriptElement")}} یک مقدار بولی است که نشان می‌دهد آیا اسکریپت باید در مرورگرهایی که از [ماژول‌های ES](/en-US/docs/Web/JavaScript/Guide/Modules) پشتیبانی می‌کنند اجرا شود یا خیر. در عمل، می‌توان از این ویژگی برای ارائه‌ی اسکریپت‌های جایگزین (fallback) به مرورگرهای قدیمی‌تری استفاده کرد که از ماژول‌های جاوااسکریپت پشتیبانی نمی‌کنند.

این ویژگی، صفت `nomodule` عنصر {{HTMLElement("script")}} را منعکس می‌کند.

## مقدار

یک مقدار بولی؛ `true` به این معناست که اسکریپت نباید در مرورگرهایی که از ماژول‌های ES پشتیبانی می‌کنند اجرا شود و `false` به این معناست که اسکریپت می‌تواند اجرا شود.

## مثال‌ها

```html
<script id="el" nomodule>
  // If the browser supports JavaScript modules, the following script will not be executed.
  console.log("The browser does not support JavaScript modules");
</script>
```

```js
const el = document.getElementById("el");
console.log(el.noModule); // Output: true
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

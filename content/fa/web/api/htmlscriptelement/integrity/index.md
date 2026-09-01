---
title: "HTMLScriptElement: integrity property"
short-title: integrity
slug: Web/API/HTMLScriptElement/integrity
page-type: web-api-instance-property
browser-compat: api.HTMLScriptElement.integrity
---

{{APIRef("HTML DOM")}}

ویژگی **`integrity`** از رابط {{domxref("HTMLScriptElement")}} یک رشته است که شامل فراداده‌های درون‌خطی می‌باشد که مرورگر می‌تواند از آن برای تأیید اینکه یک منبع واکشی‌شده بدون دستکاری غیرمنتظره تحویل داده شده است، استفاده کند.

این ویژگی منعکس‌کنندهٔ ویژگی `integrity` عنصر {{HTMLElement("script")}} است.

## مقدار

یک رشته.

## نمونه‌ها

```html
<script
  id="el"
  src="https://example.com/example-framework.js"
  integrity="sha384-oqVuAfXRKap7fdgcCY5uykM6+R9GqQ8K/uxy9rx7HNQlGYl1kPzQho1wx4JwY8wC"
  crossorigin="anonymous"></script>
```

```js
const el = document.getElementById("el");
console.log(el.integrity); // Output: "sha384-oqVuAfXRKap7fdgcCY5uykM6+R9GqQ8K/uxy9rx7HNQlGYl1kPzQho1wx4JwY8wC"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("HTMLLinkElement.integrity")}}
- [Subresource Integrity](/en-US/docs/Web/Security/Defenses/Subresource_Integrity)
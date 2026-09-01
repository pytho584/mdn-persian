---
title: "HTMLLinkElement: integrity property"
short-title: integrity
slug: Web/API/HTMLLinkElement/integrity
page-type: web-api-instance-property
browser-compat: api.HTMLLinkElement.integrity
---

{{APIRef("HTML DOM")}}

ویژگی **`integrity`** در رابط {{domxref("HTMLLinkElement")}} یک رشته است که شامل ابرداده‌های درون‌خطی (inline metadata) می‌باشد. مرورگر می‌تواند از این ابرداده برای تأیید این‌که منبع دریافت‌شده بدون دستکاری غیرمنتظره تحویل داده شده است استفاده کند.

این ویژگی منعکس‌کنندهٔ ویژگی `integrity` عنصر {{HTMLElement("link")}} است.

## مقدار

یک رشته (string).

## مثال‌ها

```html
<link
  id="el"
  href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css"
  rel="stylesheet"
  integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH"
  crossorigin="anonymous" />
```

```js
const el = document.getElementById("el");
console.log(el.integrity); // Output: "sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLScriptElement.integrity")}}
- [یکپارچگی زیرمنبع (Subresource Integrity)](/en-US/docs/Web/Security/Defenses/Subresource_Integrity)
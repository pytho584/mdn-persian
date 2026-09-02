--- 
title: "MathMLElement: nonce property"
short-title: nonce
slug: Web/API/MathMLElement/nonce
page-type: web-api-instance-property
browser-compat: api.MathMLElement.nonce
---

{{APIRef("MathML")}}

ویژگی **`nonce`** از رابط {{DOMxRef("MathMLElement")}}، مقدار {{Glossary("Nonce", "nonce")}} (یک عدد یکبارمصرف) را بازمی‌گرداند که توسط [خط مشی امنیت محتوا (CSP)](/en-US/docs/Web/HTTP/Guides/CSP) برای تعیین اینکه آیا یک درخواست خاص مجاز به ادامه است یا خیر، استفاده می‌شود.

## مقدار

یک رشته (String)؛ nonce رمزنگاری‌شده، یا یک رشته خالی اگر nonce تنظیم نشده باشد.

## مثال‌ها

### دریافت مقدار nonce

```js
const math = document.querySelector("math");
console.log(math.nonce);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLElement.nonce")}} — ویژگی مشابه برای عناصر HTML.
- {{domxref("SVGElement.nonce")}} — ویژگی مشابه برای عناصر SVG.
- [ویژگی سراسری `nonce`](/en-US/docs/Web/HTML/Reference/Global_attributes/nonce)
- [خط مشی امنیت محتوا (CSP)](/en-US/docs/Web/HTTP/Guides/CSP)
- CSP: {{CSP("script-src")}}
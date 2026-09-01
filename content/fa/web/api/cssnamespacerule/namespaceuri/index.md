---
title: "CSSNamespaceRule: namespaceURI property"
---

{{ APIRef("CSSOM") }}

خاصیت فقط-خواندنی **`namespaceURI`** از {{domxref("CSSNamespaceRule")}} یک رشته شامل متن URI فضای نام داده شده را برمی‌گرداند.

## مقدار

یک رشته شامل یک URI.

## مثال‌ها

شیوه‌نامه شامل یک فضای نام به عنوان تنها قانون است. بنابراین اولین {{domxref("CSSRule")}} برگردانده شده یک `CSSNamespaceRule` خواهد بود. مقدار خاصیت `namespaceURI` برابر با `http://www.w3.org/1999/xhtml` خواهد بود.

```css
@namespace url("http://www.w3.org/1999/xhtml");
```

```js
const myRules = document.styleSheets[0].cssRules;
console.log(myRules[0].namespaceURI); // 'http://www.w3.org/1999/xhtml'
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}
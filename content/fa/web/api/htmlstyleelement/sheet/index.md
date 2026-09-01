---
title: "HTMLStyleElement: sheet property"
short-title: sheet
slug: Web/API/HTMLStyleElement/sheet
page-type: web-api-instance-property
browser-compat: api.HTMLStyleElement.sheet
---

{{APIRef("HTML DOM")}}

ویژگی فقط-خواندنی **`sheet`** از رابط {{domxref("HTMLStyleElement")}} حاوی برگه سبک (stylesheet) مرتبط با آن عنصر است.

یک {{DOMxref("StyleSheet")}} همیشه با یک {{domxref("HTMLStyleElement")}} مرتبط است، مگر اینکه ویژگی `type` آن برابر `text/css` نباشد.

## مقدار

یک شیء {{DOMxRef("StyleSheet")}}، یا `null` اگر هیچ‌کدام با عنصر مرتبط نباشد.

## مثال‌ها

فرض کنید `<head>` شامل موارد زیر است:

```html
<style id="inline-style">
  p {
    color: blue;
  }
</style>
```

ویژگی `sheet` شیء `HTMLStyleElement` مرتبط، شیء {{domxref("StyleSheet")}} توصیف‌کننده آن را برمی‌گرداند.

```js
const style = document.getElementById("inline-style");
console.log(style.sheet.cssRules[0].cssText); // 'p { color: blue; }'
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}
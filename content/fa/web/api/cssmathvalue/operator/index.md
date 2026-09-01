---
title: "CSSMathValue: operator property"
short-title: operator
slug: Web/API/CSSMathValue/operator
page-type: web-api-instance-property
browser-compat: api.CSSMathValue.operator
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`operator`** در رابط {{domxref("CSSMathValue")}} عملگری را برمی‌گرداند که زیرنوع فعلی نشان‌دهندهٔ آن است.
برای مثال، اگر زیرنوع فعلی `CSSMathValue` از نوع `CSSMathSum` باشد، این ویژگی رشتهٔ `"sum"` را برمی‌گرداند.

## مقدار

یک {{jsxref('String')}}.

| رابط                           | مقدار        |
| ------------------------------ | ------------ |
| {{domxref('CSSMathSum')}}      | `"sum"`      |
| {{domxref('CSSMathProduct')}}  | `"product"`  |
| {{domxref('CSSMathMin')}}      | `"min"`      |
| {{domxref('CSSMathMax')}}      | `"max"`      |
| {{domxref('CSSMathClamp')}}    | `"clamp"`    |
| {{domxref('CSSMathNegate')}}   | `"negate"`   |
| {{domxref('CSSMathInvert')}}   | `"invert"`   |

## مثال‌ها

### استفادهٔ پایه

این مثال نشان می‌دهد که ویژگی `operator` چگونه عملگرِ نمایش‌داده‌شده توسط زیرنوع `CSSMathValue` یک مقدار {{cssxref("calc()")}} را شناسایی می‌کند، از جمله برای یک مقدار تو در تو.

#### HTML

```html
<div id="demoBox">Text</div>
```

```html hidden
<pre id="log"></pre>
```

#### CSS

`width` با استفاده از یک تفریق `calc()` تنظیم شده است که به صورت یک `CSSMathSum` نمایش داده می‌شود و جملهٔ دوم آن منفی شده است.

```css
#demoBox {
  width: calc(50% - 0.5vw);
}
```

```css hidden
#log {
  height: 80px;
  overflow: scroll;
  padding: 0.5rem;
  border: 1px solid black;
}
```

#### JavaScript

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText += `${text}\n`;
}
```

مقدار `width` را با استفاده از {{domxref("Element.computedStyleMap()", "computedStyleMap()")}} می‌خوانیم و سپس `operator` آن و `operator` مقدار تودرتو را ثبت می‌کنیم.

```js
const styleMap = document.querySelector("#demoBox").computedStyleMap();
const width = styleMap.get("width");

log(`operator: ${width.operator}`);
log(`nested value operator: ${width.values[1].operator}`);
```

#### نتیجه

`width` توسط یک شیء `CSSMathSum` نمایش داده می‌شود که `operator` آن `"sum"` است، زیرا `calc(50% - 0.5vw)` به صورت جمع `50%` و نفی `0.5vw` نمایش داده می‌شود.
`operator` مقدار تودرتوی دوم `"negate"` است که این نفی را بازتاب می‌دهد.

{{EmbedLiveSample("Basic usage", 300, 170)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
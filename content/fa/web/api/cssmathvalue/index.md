---
title: "CSSMathValue"
---

---
title: CSSMathValue
slug: Web/API/CSSMathValue
page-type: web-api-interface
browser-compat: api.CSSMathValue
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

اینترفیسِ **`CSSMathValue`** از [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Object_Model)، اینترفیس پایه برای اشیایی است که مقادیر عددیِ پیچیدهٔ تولیدشده توسط توابع CSS {{cssxref("calc()")}}، {{cssxref("min()")}}، {{cssxref("max()")}} و {{cssxref("clamp()")}} را نشان می‌دهند.

> [!NOTE]
> `CSSMathValue` نمی‌تواند به‌طور مستقیم ساخته شود.
> نمونه‌ها توسط پلتفرم (مثلاً از طریق {{domxref("StylePropertyMapReadOnly.get()")}}) به‌عنوان یکی از زیرانواعِ آن، که در ادامه فهرست شده‌اند، بازگردانده می‌شوند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref('CSSMathValue.operator')}} {{ReadOnlyInline}}
  - : عملگری را که زیرنوعِ فعلی نشان می‌دهد، برمی‌گرداند.

## متدهای ایستا

_همچنین متدهایی را از اینترفیس والد خود، {{DOMxRef("CSSNumericValue")}}، به ارث می‌برد._

## متدهای نمونه

_همچنین متدهایی را از اینترفیس والد خود، {{DOMxRef("CSSNumericValue")}}، به ارث می‌برد._

## اینترفیس‌های مبتنی بر CSSMathValue

- {{DOMxRef('CSSMathClamp')}}
- {{domxref('CSSMathInvert')}}
- {{domxref('CSSMathMax')}}
- {{domxref('CSSMathMin')}}
- {{domxref('CSSMathNegate')}}
- {{domxref('CSSMathProduct')}}
- {{domxref('CSSMathSum')}}

## مثال‌ها

### بازنمایی‌های `calc()`

این مثال نشان می‌دهد که ویژگی {{domxref("CSSMathValue.operator", "operator")}} چگونه عملیاتِ بازنمایی‌شده توسط زیرنوعِ `CSSMathValue` یک مقدار {{cssxref("calc()")}} را شناسایی می‌کند؛ از جمله برای یک مقدار تودرتو.

#### HTML

```html
<div id="demoBox">Text</div>
```

```html hidden
<pre id="log"></pre>
```

#### CSS

مقدار `width` با استفاده از یک تفریق `calc()` تنظیم می‌شود، که به‌صورت یک `CSSMathSum` بازنمایی می‌شود و جملهٔ دوم آن نفی شده است.

```css
#demoBox {
  width: calc(30% - 20px);
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

مقدار `width` را با استفاده از {{domxref("Element.computedStyleMap()", "computedStyleMap()")}} می‌خوانیم و سپس `operator` آن و `operator` مقدار تودرتوی آن را در خروجی ثبت می‌کنیم.

```js
const styleMap = document.querySelector("#demoBox").computedStyleMap();
const width = styleMap.get("width");

log(`type: ${width.constructor.name}`);
log(`operator: ${width.operator}`);
log(`nested value type: ${width.values[1].constructor.name}`);
log(`nested value operator: ${width.values[1].operator}`);
```

#### نتیجه

`width` توسط یک شیءِ `CSSMathSum` بازنمایی می‌شود که `operator` آن `"sum"` است؛ زیرا `calc(30% - 20px)` به‌صورت جمعِ `30%` و نفیِ `20px` بازنمایی می‌شود. نوعِ دومین مقدار تودرتو `CSSMathNegate` است و `operator` آن `"negate"` است (که منعکس‌کنندهٔ همان نفی است).

{{EmbedLiveSample("`calc()` representations", 300, 170)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
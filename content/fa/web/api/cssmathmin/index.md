---
title: CSSMathMin
slug: Web/API/CSSMathMin
page-type: web-api-interface
browser-compat: api.CSSMathMin
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

**`CSSMathMin`** رابط [API مدل شیء تایپ‌شده CSS](/en-US/docs/Web/API/CSS_Object_Model) تابع CSS {{CSSXref('min','min()')}} را نشان می‌دهد.

{{InheritanceDiagram}}

## سازنده

- {{domxref("CSSMathMin.CSSMathMin", "CSSMathMin()")}} {{Experimental_Inline}}
  - : یک شیء جدید `CSSMathMin` می‌سازد.

## ویژگی‌های نمونه

_همچنین ویژگی‌های رابط والد خود، {{DOMxRef("CSSMathValue")}} را به ارث می‌برد._

- {{domxref('CSSMathMin.values')}} {{ReadOnlyInline}}
  - : یک شیء {{domxref('CSSNumericArray')}} برمی‌گرداند که شامل یک یا چند شیء {{domxref('CSSNumericValue')}} است.

## روش‌های ایستا

_همچنین روش‌های رابط والد خود، {{DOMxRef("CSSMathValue")}} را به ارث می‌برد._

## روش‌های نمونه

_همچنین روش‌های رابط والد خود، {{DOMxRef("CSSMathValue")}} را به ارث می‌برد._

## توضیحات

تابع CSS {{cssxref("min", "min()")}} یک یا چند مقدار جدا شده با کاما را به عنوان آرگومان می‌گیرد و کوچک‌ترین آن‌ها را برمی‌گرداند.

اگر همه آرگومان‌ها مقادیر مطلق باشند، مانند طول‌های پیکسلی، `min()` در زمان تجزیه به یک مقدار واحد تبدیل می‌شود که توسط مدل شیء تایپ‌شده CSS به صورت یک {{domxref("CSSUnitValue")}} نمایش داده می‌شود.
اگر عبارت `min()` را نتوان در زمان تجزیه به یک مقدار واحد تبدیل کرد (مثلاً چون یکی از آرگومان‌های آن از یک واحد نسبی مانند `vw` یا `%` استفاده می‌کند)، آن تابع به صورت یک شیء `CSSMathMin` نمایش داده می‌شود و آرگومان‌های ارسال‌شده به `min()` (یا به سازنده `CSSMathMin()`) به عنوان ویژگی `values` در دسترس هستند.

توجه داشته باشید که `CSSMathMin` تابع `min()` را نشان می‌دهد، نه مقدار نهایی آن را.
برای تعیین مقدار یک ویژگی با استفاده از `min()`، باید سبک محاسبه‌شده آن را بخوانید (مثلاً با {{domxref("Window.getComputedStyle", "getComputedStyle()")}}).

## مثال‌ها

### استفاده اساسی

کد زیر یک نمونه `CSSMathMin` از سه مقدار ایجاد می‌کند و سپس ویژگی‌های `operator` و `values` آن را بازخوانی می‌کند.

```js
const min = new CSSMathMin(CSS.px(10), CSS.em(5), CSS.percent(50));

console.log(min.constructor.name); // "CSSMathMin"
console.log(min.operator); // 'min'
console.log(min.values);
// CSSNumericArray {0: CSSUnitValue, 1: CSSUnitValue, 2: CSSUnitValue, length: 3}
console.log(min.values[0]); // CSSUnitValue {value: 10, unit: "px"}
```

### نمایش‌های تابع `min()`

این مثال نشان می‌دهد که چگونه {{cssxref("min", "min()")}} بسته به اینکه همه آرگومان‌های آن مقادیر مطلق باشند یا نه، توسط یک {{domxref("CSSUnitValue")}} یا یک `CSSMathMin` نمایش داده می‌شود.

#### HTML

```html
<div id="demoBox">Text</div>
```

```html hidden
<pre id="log"></pre>
```

#### CSS

`width` با استفاده از `min()` تنظیم شده است که همه آرگومان‌های آن طول‌های مطلق هستند، بنابراین مرورگر می‌تواند بلافاصله آن را به یک مقدار ثابت واحد تبدیل کند.
`font-size` با استفاده از `min()` تنظیم شده است که یک آرگومان آن از واحد نسبی `vw` استفاده می‌کند، بنابراین مرورگر تا زمان چیدمان نمی‌تواند آن را حل کند (این مورد با یک `CSSMathMin` نمایش داده می‌شود).

```css
#demoBox {
  width: min(10px, 50px);
  font-size: min(1rem, 5vw);
}
```

```css hidden
#log {
  height: 200px;
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

ابتدا شیوه‌نامه عنصر جعبه نمایشی را پیدا می‌کنیم و مقادیر `width` و `font-size` آن را با {{domxref("CSSStyleRule.styleMap", "styleMap")}} می‌خوانیم.

```js
const demoBox = document.querySelector("#demoBox");

const rules = document.getElementById("css-output").sheet.cssRules;
const rule = [...rules].find((r) => r.selectorText === "#demoBox");
const styleMap = rule.styleMap;
const width = styleMap.get("width");
const fontSize = styleMap.get("font-size");
```

سپس نوع و مقدار نمایش‌های CSS OM تایپ‌شده را همراه با مقادیر محاسبه‌شده (نهایی) ثبت می‌کنیم.

```js
log("width");
log(` type: ${width.constructor.name}`);
log(` value: ${width}`);
log(` resolved: ${getComputedStyle(demoBox).width}`);

log("\nfont-size");
log(` type: ${fontSize.constructor.name}`);
log(` values: [${[...fontSize.values].join(", ")}]`);
log(` resolved: ${getComputedStyle(demoBox).fontSize}`);
```

#### نتیجه

`width` توسط یک شیء `CSSUnitValue` نمایش داده می‌شود که مقدار آن با عرض نهایی مطابقت دارد.
`font-size` توسط یک شیء `CSSMathMin` نمایش داده می‌شود که عملوندهای اصلی تابع `min()` را در معرض دید قرار می‌دهد.

{{EmbedLiveSample("`min()` representations", 300, 300)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}
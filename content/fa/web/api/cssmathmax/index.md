---
title: CSSMathMax
slug: Web/API/CSSMathMax
page-type: web-api-interface
browser-compat: api.CSSMathMax
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

رابط **`CSSMathMax`** در [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Object_Model) نشان‌دهنده تابع {{CSSXref('max','max()')}} در CSS است.

{{InheritanceDiagram}}

## سازنده

- {{domxref("CSSMathMax.CSSMathMax", "CSSMathMax()")}} {{Experimental_Inline}}
  - : یک شیء `CSSMathMax` جدید ایجاد می‌کند.

## ویژگی‌های نمونه

_همچنین ویژگی‌هایی را از رابط والد خود، {{DOMxRef("CSSMathValue")}}، به ارث می‌برد._

- {{domxref('CSSMathMax.values')}} {{ReadOnlyInline}}
  - : یک شیء {{domxref('CSSNumericArray')}} برمی‌گرداند که شامل یک یا چند شیء {{domxref('CSSNumericValue')}} است.

## روش‌های ایستا

_همچنین روش‌هایی را از رابط والد خود، {{DOMxRef("CSSMathValue")}}، به ارث می‌برد._

## روش‌های نمونه

_همچنین روش‌هایی را از رابط والد خود، {{DOMxRef("CSSMathValue")}}، به ارث می‌برد._

## توضیحات

تابع {{cssxref("max", "max()")}} در CSS یک یا چند مقدار جدا شده با کاما را به عنوان آرگومان می‌گیرد و بزرگترین آن‌ها را برمی‌گرداند.

اگر همه آرگومان‌ها مقادیر مطلق (مانند طول‌های پیکسلی) باشند، `max()` در زمان تجزیه به یک مقدار واحد تبدیل می‌شود که توسط CSS Typed Object Model به صورت یک {{domxref("CSSUnitValue")}} نمایش داده می‌شود.
اگر عبارت `max()` نتواند در زمان تجزیه به یک مقدار واحد تبدیل شود (مثلاً به دلیل استفاده از یک واحد نسبی مانند `vw` یا `%` در یکی از آرگومان‌ها)، تابع به صورت یک شیء `CSSMathMax` نمایش داده می‌شود و آرگومان‌های ارسال‌شده به `max()` (یا به سازنده `CSSMathMax()`) به عنوان ویژگی `values` در دسترس قرار می‌گیرند.

توجه داشته باشید که `CSSMathMax` نشان‌دهنده خود تابع `max()` است، نه مقدار حل‌شده آن. برای تعیین مقدار یک ویژگی با استفاده از `max()`، باید سبک محاسبه‌شده آن را بخوانید (مثلاً با {{domxref("Window.getComputedStyle", "getComputedStyle()")}}).

## مثال‌ها

### استفاده پایه

کد زیر یک نمونه `CSSMathMax` از سه مقدار ایجاد می‌کند و سپس ویژگی‌های `operator` و `values` آن را می‌خواند.

```js
const max = new CSSMathMax(CSS.px(10), CSS.em(5), CSS.percent(50));

console.log(max.constructor.name); // "CSSMathMax"
console.log(max.operator); // 'max'
console.log(max.values); // CSSNumericArray {0: CSSUnitValue, 1: CSSUnitValue, 2: CSSUnitValue, length: 3}
console.log(max.values[0]); // CSSUnitValue {value: 10, unit: "px"}
```

### نمایش‌های `max()`

این مثال نشان می‌دهد که چگونه {{cssxref("max", "max()")}} بسته به اینکه همه آرگومان‌های آن مقادیر مطلق باشند یا نه، توسط یک {{domxref("CSSUnitValue")}} یا یک `CSSMathMax` نمایش داده می‌شود.

#### HTML

```html
<div id="demoBox">Text</div>
```

```html hidden
<pre id="log"></pre>
```

#### CSS

`width` با استفاده از یک `max()` تنظیم شده است که آرگومان‌های آن همه طول‌های مطلق هستند، بنابراین مرورگر می‌تواند بلافاصله آن را به یک مقدار ثابت واحد تبدیل کند.
`font-size` با استفاده از یک `max()` تنظیم شده است که در آن یکی از آرگومان‌ها از واحد نسبی `vw` استفاده می‌کند، بنابراین مرورگر نمی‌تواند آن را تا زمان چیدمان حل کند (این مورد با یک `CSSMathMax` نمایش داده می‌شود).

```css
#demoBox {
  width: max(10px, 50px);
  font-size: max(1rem, 5vw);
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

ابتدا قاعده سبک جعبه دمو را پیدا کرده و مقادیر `width` و `font-size` آن را با استفاده از {{domxref("CSSStyleRule.styleMap", "styleMap")}} می‌خوانیم.

```js
const demoBox = document.querySelector("#demoBox");

const rules = document.getElementById("css-output").sheet.cssRules;
const rule = [...rules].find((r) => r.selectorText === "#demoBox");
const styleMap = rule.styleMap;
const width = styleMap.get("width");
const fontSize = styleMap.get("font-size");
```

سپس نوع و مقدار نمایش‌های CSS Typed OM را به همراه مقادیر محاسبه‌شده (حل‌شده) ثبت می‌کنیم.

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

`width` توسط یک شیء `CSSUnitValue` نمایش داده می‌شود که مقداری برابر با عرض حل‌شده دارد.
`font-size` توسط یک شیء `CSSMathMax` نمایش داده می‌شود که عملوندهای اصلی تابع `max()` را در معرض دید قرار می‌دهد.

{{EmbedLiveSample("`max()` representations", 300, 300)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}
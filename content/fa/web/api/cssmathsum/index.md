---
title: CSSMathSum
slug: Web/API/CSSMathSum
page-type: web-api-interface
browser-compat: api.CSSMathSum
---

{{APIRef("CSS Typed Object Model API")}}{{AvailableInWorkers}}

رابط **`CSSMathSum`** در [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Object_Model) مجموع دو یا چند مقدار {{domxref('CSSNumericValue')}} را نشان می‌دهد — در مواردی که نتیجه را نمی‌توان به صورت یک مقدار واحد نمایش داد.

{{InheritanceDiagram}}

## Constructor

- {{domxref("CSSMathSum.CSSMathSum", "CSSMathSum()")}} {{Experimental_Inline}}
  - : یک شیء جدید `CSSMathSum` می‌سازد.

## Instance properties

_Also inherits properties from its parent interface, {{DOMxRef("CSSMathValue")}}._

- {{domxref('CSSMathSum.values')}} {{ReadOnlyInline}}
  - : یک شیء {{domxref('CSSNumericArray')}} برمی‌گرداند که شامل یک یا چند شیء {{domxref('CSSNumericValue')}} است.

## Static methods

_Also inherits methods from its parent interface, {{DOMxRef("CSSMathValue")}}._

## Instance methods

_Also inherits methods from its parent interface, {{DOMxRef("CSSMathValue")}}._

## Description

یک `CSSMathSum` هر زمان ساخته می‌شود که یک جمع یا تفریق نتواند به یک مقدار واحد تبدیل شود — برای مثال، وقتی عملوندها واحدهای متفاوتی دارند، مانند طول و درصد.

فراخوانی {{domxref('CSSNumericValue.add','add()')}} یا {{domxref('CSSNumericValue.sub','sub()')}} روی عملوندهایی که نمی‌توان آن‌ها را ترکیب کرد، یک `CSSMathSum` برمی‌گرداند؛ اگر همهٔ عملوندها واحد یکسانی داشته باشند، بلافاصله به یک {{domxref('CSSUnitValue')}} واحد تبدیل می‌شوند. در مقابل، {{domxref('CSSNumericValue.toSum','toSum()')}} همیشه یک `CSSMathSum` برمی‌گرداند، حتی وقتی بتوان عبارت‌های آن را در یک مقدار واحد ترکیب کرد.

[`StylePropertyMapReadOnly.get()`](/en-US/docs/Web/API/StylePropertyMapReadOnly/get) نیز به همین شکل یک `CSSMathSum` برمی‌گرداند — برای یک مقدار {{cssxref("calc()")}} که به جمع یا تفریقی تبدیل می‌شود که نمی‌توان آن را در یک مقدار واحد ترکیب کرد.

`CSSMathSum` خودِ عبارت جمع را نشان می‌دهد، نه مقدار نهایی (resolved). برای دریافت مقدار نهایی، از {{domxref("Window.getComputedStyle", "getComputedStyle()")}} استفاده کنید.

## Examples

### Basic usage

کد زیر یک نمونهٔ `CSSMathSum` از سه مقدار می‌سازد و سپس ویژگی‌های `operator` و `values` آن را بازخوانی می‌کند.

```js
const sum = new CSSMathSum(CSS.px(10), CSS.em(5), CSS.percent(50));

console.log(sum.constructor.name); // "CSSMathSum"
console.log(sum.operator); // 'sum'

console.log(sum.values); // CSSNumericArray {0: CSSUnitValue, 1: CSSUnitValue, 2: CSSUnitValue, length: 3}
console.log(sum.values[0]); // CSSUnitValue {value: 10, unit: "px"}
```

### `calc()` representations

این مثال نشان می‌دهد که یک جمع {{cssxref("calc()")}} چگونه به صورت یک {{domxref("CSSUnitValue")}} یا یک `CSSMathSum` نمایش داده می‌شود، بسته به اینکه عبارت‌های آن واحد مشترکی داشته باشند یا نه.

#### HTML

```html
<div id="demoBox">Text</div>
```

```html hidden
<pre id="log"></pre>
```

#### CSS

مقدار `width` با یک جمع `calc()` تنظیم شده است که هر دو عبارت آن طول‌های `px` هستند، بنابراین مرورگر می‌تواند بلافاصله آن را به یک مقدار ثابت واحد تبدیل کند. مقدار `font-size` با یک جمع `calc()` تنظیم شده است که واحدهای `rem` و `vw` را ترکیب می‌کند، بنابراین مرورگر نمی‌تواند عبارت‌های آن را تا زمان چیدمان (layout) با هم ترکیب کند (این با یک `CSSMathSum` نمایش داده می‌شود).

```css
#demoBox {
  width: calc(10px + 5px);
  font-size: calc(1rem + 5vw);
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

ابتدا قانون سبکِ جعبهٔ نمونه را پیدا می‌کنیم و مقادیر `width` و `font-size` آن را با استفاده از {{domxref("CSSStyleRule.styleMap", "styleMap")}} می‌خوانیم.

```js
const demoBox = document.querySelector("#demoBox");

const rules = document.getElementById("css-output").sheet.cssRules;
const rule = [...rules].find((r) => r.selectorText === "#demoBox");
const styleMap = rule.styleMap;
const width = styleMap.get("width");
const fontSize = styleMap.get("font-size");
```

سپس نوع و مقدارِ نمایش‌های CSS Typed OM را ثبت (log) می‌کنیم و پس از آن مقادیر محاسبه‌شده (resolved) را.

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

#### Result

`width` با یک شیء `CSSUnitValue` نمایش داده می‌شود که مقدار آن با عرضِ نهایی (resolved) مطابقت دارد. `font-size` با یک شیء `CSSMathSum` نمایش داده می‌شود که عبارت‌های اصلی جمع `calc()` را آشکار می‌کند.

{{EmbedLiveSample("`calc()` representations", 300, 300)}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("CSSNumericValue.add", "add()")}}
- {{domxref("CSSNumericValue.sub", "sub()")}}
- {{domxref("CSSNumericValue.toSum", "toSum()")}}
- {{domxref("CSSMathValue.operator")}}
- {{domxref("CSSMathNegate")}}
- {{domxref("CSSMathProduct")}}
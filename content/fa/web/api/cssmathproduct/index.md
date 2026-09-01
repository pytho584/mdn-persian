---
title: "CSSMathProduct"
---

---
title: CSSMathProduct
slug: Web/API/CSSMathProduct
page-type: web-api-interface
browser-compat: api.CSSMathProduct
---

{{APIRef("CSS Typed Object Model API")}}{{AvailableInWorkers}}

رابطهٔ **`CSSMathProduct`** در [API مدل شیء تایپ‌شدهٔ CSS](/en-US/docs/Web/API/CSS_Object_Model)، حاصل‌ضرب دو یا چند مقدار {{domxref('CSSNumericValue')}} را نشان می‌دهد — در مواردی که نتیجه را نمی‌توان به‌صورت یک مقدار واحد نمایش داد.

{{InheritanceDiagram}}

## سازنده

- {{domxref("CSSMathProduct.CSSMathProduct", "CSSMathProduct()")}} {{Experimental_Inline}}
  - : یک شیء `CSSMathProduct` جدید می‌سازد.

## ویژگی‌های نمونه

_همچنین ویژگی‌های رابط والد خود، {{DOMxRef("CSSMathValue")}} را به ارث می‌برد._

- {{domxref('CSSMathProduct.values')}} {{ReadOnlyInline}}
  - : یک شیء {{domxref('CSSNumericArray')}} برمی‌گرداند که شامل یک یا چند شیء {{domxref('CSSNumericValue')}} است.

## روش‌های ایستا

_همچنین روش‌های رابط والد خود، {{DOMxRef("CSSMathValue")}} را به ارث می‌برد._

## روش‌های نمونه

_همچنین روش‌های رابط والد خود، {{DOMxRef("CSSMathValue")}} را به ارث می‌برد._

## توضیحات

یک `CSSMathProduct` زمانی تولید می‌شود که یک ضرب یا تقسیم نتواند به یک مقدار واحد ساده‌سازی شود — این اتفاق زمانی می‌افتد که بیش از یک عملوند دارای واحد باشد، مثلاً ضرب دو طول (`10px * 20px`) یا ضرب یک طول در یک درصد، به‌جای ضرب یک مقدار در یک عدد ساده.

فراخوانی {{domxref('CSSNumericValue.mul','mul()')}} یا {{domxref('CSSNumericValue.div','div()')}} روی عملوندهایی که قابل ترکیب نیستند، یک `CSSMathProduct` برمی‌گرداند؛ اگر همهٔ عملوندها اعداد ساده باشند یا همه به‌جز یکی از آن‌ها ساده باشند، بلافاصله به یک {{domxref('CSSUnitValue')}} واحد تبدیل می‌شوند.

[`StylePropertyMapReadOnly.get()`](/en-US/docs/Web/API/StylePropertyMapReadOnly/get) نیز به همین ترتیب یک `CSSMathProduct` برمی‌گرداند — برای یک مقدار {{cssxref("calc()")}} که به ضرب یا تقسیمی منجر می‌شود که نمی‌توان آن را در یک مقدار واحد ترکیب کرد.

`CSSMathProduct` خودِ عبارت حاصل‌ضرب را نشان می‌دهد، نه یک مقدار نهایی محاسبه‌شده.
برای دریافت مقدار نهایی، از {{domxref("Window.getComputedStyle", "getComputedStyle()")}} استفاده کنید.

## مثال‌ها

### کاربرد پایه

کد زیر یک نمونهٔ `CSSMathProduct` از دو مقدار می‌سازد و سپس ویژگی‌های `operator` و `values` آن را می‌خواند.

```js
const product = new CSSMathProduct(CSS.px(10), CSS.percent(50));

console.log(product.constructor.name); // "CSSMathProduct"
console.log(product.operator); // 'product'
console.log(product.values); // CSSNumericArray {0: CSSUnitValue, 1: CSSUnitValue, length: 2}
console.log(product.values[0]); // CSSUnitValue {value: 10, unit: "px"}
```

### بازنمایی‌های `calc()`

این مثال نشان می‌دهد که یک ضرب {{cssxref("calc()")}} چگونه توسط یک {{domxref("CSSUnitValue")}} یا یک `CSSMathProduct` نمایش داده می‌شود، بسته به اینکه آیا می‌توان آن را به یک مقدار واحد ساده‌سازی کرد یا نه.

#### HTML

```html
<div id="demoBox">Text</div>
```

```html hidden
<pre id="log"></pre>
```

#### CSS

`width` با استفاده از یک حاصل‌ضرب `calc()` شامل یک طول و یک عدد ساده تنظیم شده است، بنابراین مرورگر می‌تواند بلافاصله آن را به یک مقدار ثابت واحد تبدیل کند.
`font-size` با استفاده از یک حاصل‌ضرب `calc()` تنظیم شده است که یک عدد ساده را در یک مجموع داخل پرانتز شامل `1rem` و `5vw` ضرب می‌کند؛ از آنجا که خودِ مجموع را نمی‌توان به یک مقدار واحد ترکیب کرد (واحدها متفاوت هستند)، حاصل‌ضرب نیز نمی‌تواند، و این توسط یک `CSSMathProduct` نمایش داده می‌شود.

```css
#demoBox {
  width: calc(10px * 2);
  font-size: calc(2 * (1rem + 5vw));
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

ابتدا قانون سبک مربوط به جعبهٔ demo را پیدا می‌کنیم و مقادیر `width` و `font-size` آن را با استفاده از {{domxref("CSSStyleRule.styleMap", "styleMap")}} می‌خوانیم.

```js
const demoBox = document.querySelector("#demoBox");

const rules = document.getElementById("css-output").sheet.cssRules;
const rule = [...rules].find((r) => r.selectorText === "#demoBox");
const styleMap = rule.styleMap;
const width = styleMap.get("width");
const fontSize = styleMap.get("font-size");
```

سپس نوع و مقدار بازنمایی‌های CSS Typed OM را ثبت می‌کنیم و به‌دنبال آن مقادیر نهایی محاسبه‌شده (resolved) را.

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

`width` توسط یک شیء `CSSUnitValue` نمایش داده می‌شود که مقداری مطابق با عرض نهایی دارد.
`font-size` توسط یک شیء `CSSMathProduct` نمایش داده می‌شود که عبارت‌های اصلیِ حاصل‌ضرب `calc()` را در دسترس قرار می‌دهد.

{{EmbedLiveSample("`calc()` representations", 300, 300)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CSSNumericValue.mul", "mul()")}}
- {{domxref("CSSNumericValue.div", "div()")}}
- {{domxref("CSSMathValue.operator")}}
- {{domxref("CSSMathInvert")}}
- {{domxref("CSSMathSum")}}
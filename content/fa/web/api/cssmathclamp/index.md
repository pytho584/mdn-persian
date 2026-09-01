---
title: "CSSMathClamp"
slug: Web/API/CSSMathClamp
page-type: web-api-interface
browser-compat: api.CSSMathClamp
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

رابط **`CSSMathClamp`** از [API مدل شیء تایپ‌شده CSS](/en-US/docs/Web/API/CSS_Object_Model) تابع CSS {{CSSXref("clamp","clamp()")}} را نمایش می‌دهد.

{{InheritanceDiagram}}

## سازنده

- {{domxref("CSSMathClamp.CSSMathClamp", "CSSMathClamp()")}}
  - : یک شیء `CSSMathClamp` جدید ایجاد می‌کند.

## ویژگی‌های نمونه

_همچنین ویژگی‌های رابط والد خود، {{DOMxRef("CSSMathValue")}} را به ارث می‌برد._

- {{domxref("CSSMathClamp.lower")}} {{readonlyinline}}
  - : یک شیء {{domxref("CSSNumericValue")}} حاوی مقدار حداقل را برمی‌گرداند.
- {{domxref("CSSMathClamp.value")}} {{readonlyinline}}
  - : یک شیء {{domxref("CSSNumericValue")}} حاوی مقدار ترجیحی را برمی‌گرداند.
- {{domxref("CSSMathClamp.upper")}} {{readonlyinline}}
  - : یک شیء {{domxref("CSSNumericValue")}} حاوی مقدار حداکثر را برمی‌گرداند.

## روش‌های ایستا

_همچنین روش‌های رابط والد خود، {{DOMxRef("CSSMathValue")}} را به ارث می‌برد._

## روش‌های نمونه

_همچنین روش‌های رابط والد خود، {{DOMxRef("CSSMathValue")}} را به ارث می‌برد._

## توضیحات

تابع CSS {{CSSXref("clamp", "clamp()")}} سه آرگومان می‌گیرد: یک مقدار حداقل، یک مقدار ترجیحی و یک مقدار حداکثر، و مقدار ترجیحی را برمی‌گرداند که در بین حداقل و حداکثر محدود شده است.

اگر هر سه آرگومان مقادیر مطلق باشند، مانند طول‌های پیکسلی، `clamp()` در زمان تجزیه به یک مقدار واحد تبدیل می‌شود که توسط مدل شیء تایپ‌شده CSS به صورت یک {{domxref("CSSUnitValue")}} نمایش داده می‌شود. اگر عبارت `clamp()` نتواند در زمان تجزیه به یک مقدار واحد تبدیل شود (مثلاً به دلیل اینکه یکی از آرگومان‌های آن از یک واحد نسبی مانند `vw` یا `%` استفاده می‌کند)، تابع به صورت یک شیء `CSSMathClamp` نمایش داده می‌شود و سه آرگومان ارسال‌شده به `clamp()` (یا به سازنده `CSSMathClamp()`) به عنوان ویژگی‌های `lower`، `value` و `upper` در معرض دید قرار می‌گیرند.

توجه داشته باشید که `CSSMathClamp` تابع `clamp()` را نمایش می‌دهد، نه مقدار حل‌شده آن. برای تعیین مقدار یک ویژگی محدودشده، باید سبک محاسبه‌شده آن را بخوانید (مثلاً با {{domxref("Window.getComputedStyle", "getComputedStyle()")}}).

## مثال‌ها

### استفاده پایه

کد زیر یک نمونه `CSSMathClamp` از سه طول ایجاد می‌کند و سپس ویژگی‌های `lower`، `value` و `upper` آن را بازخوانی می‌کند.

```js
const clamp = new CSSMathClamp(CSS.px(10), CSS.percent(50), CSS.px(500));

console.log(clamp.constructor.name); // "CSSMathClamp"
console.log(clamp.lower); // CSSUnitValue {value: 10, unit: "px"}
console.log(clamp.value); // CSSUnitValue {value: 50, unit: "percent"}
console.log(clamp.upper); // CSSUnitValue {value: 500, unit: "px"}
```

### نمایش‌های `clamp()`

این مثال نشان می‌دهد که چگونه {{CSSXref("clamp","clamp()")}} توسط یک {{domxref("CSSUnitValue")}} یا یک `CSSMathClamp` نمایش داده می‌شود، بسته به اینکه آیا همه آرگومان‌های آن مقادیر مطلق هستند یا خیر.

#### HTML

ابتدا یک عنصر {{htmlelement("div")}} به نام `#demoBox` تعریف می‌کنیم که روی آن برخی ویژگی‌های محدودشده را تنظیم خواهیم کرد.

```html
<div id="demoBox">Text</div>
```

```html hidden
<pre id="log"></pre>
```

#### CSS

عرض جعبه با استفاده از یک `clamp()` تنظیم شده است که هر سه آرگومان آن طول‌های مطلق هستند، بنابراین مرورگر می‌تواند بلافاصله آن را به یک مقدار ثابت واحد تبدیل کند. `font-size` با استفاده از یک `clamp()` تنظیم شده است که مقدار ترجیحی آن از واحد نسبی `vw` استفاده می‌کند، بنابراین مرورگر نمی‌تواند آن را تا زمان چیدمان حل کند (این به صورت یک `CSSMathClamp` نمایش داده می‌شود).

```css
#demoBox {
  width: clamp(10px, 50px, 500px);
  font-size: clamp(1rem, 5vw, 3rem);
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

ابتدا قانون سبک جعبه آزمایشی را پیدا می‌کنیم و مقادیر `width` و `font-size` آن را با استفاده از {{domxref("CSSStyleRule.styleMap", "styleMap")}} می‌خوانیم.

```js
const demoBox = document.querySelector("#demoBox");

const rules = document.getElementById("css-output").sheet.cssRules;
const rule = [...rules].find((r) => r.selectorText === "#demoBox");
const styleMap = rule.styleMap;
const width = styleMap.get("width");
const fontSize = styleMap.get("font-size");
```

سپس نوع و مقدار نمایش‌های OM تایپ‌شده CSS و به دنبال آن مقادیر محاسبه‌شده (حل‌شده) را ثبت می‌کنیم.

```js
log("width");
log(` type: ${width.constructor.name}`);
log(` value: ${width}`);
log(` resolved: ${getComputedStyle(demoBox).width}`);

log("\nfont-size");
log(` type: ${fontSize.constructor.name}`);
log(` lower: ${fontSize.lower}`);
log(` value: ${fontSize.value}`);
log(` upper: ${fontSize.upper}`);
log(` resolved: ${getComputedStyle(demoBox).fontSize}`);
```

#### نتیجه

`width` به صورت یک `CSSUnitValue` واحد ثبت می‌شود، و مقدار حل‌شده آن مستقیماً با آن مقدار مطابقت دارد. `font-size` به صورت یک `CSSMathClamp` ثبت می‌شود و عملوندهای اصلی تابع `clamp()` را آشکار می‌کند.

{{EmbedLiveSample("`clamp()` representations", 300, 300)}}

### بازرسی یک مقدار محدودشده

این مثال از سه لغزنده محدوده برای تنظیم مقادیر `lower`، `preferred` و `upper` یک `CSSMathClamp` استفاده می‌کند، سپس آن را با استفاده از {{domxref("StylePropertyMap.set", "attributeStyleMap.set()")}} به عرض یک جعبه اعمال می‌کند. این به شما امکان می‌دهد اثر تغییر محدوده بر مقدار محدودشده `width` را مشاهده کنید.

کشیدن یک لغزنده، چیزی را که `lower`، `value` و `upper` گزارش می‌دهند تغییر می‌دهد، زیرا آنها همیشه سه عملوند ارسال‌شده به `CSSMathClamp` را منعکس می‌کنند – توجه داشته باشید که `value` بر حسب `vw` گزارش می‌شود، نه پیکسل‌های نشان‌داده‌شده روی لغزنده آن. خروجی کنار لغزنده ترجیحی هم مقدار پیکسلی و هم معادل `vw` که در واقع به سازنده ارسال شده است را نشان می‌دهد، بنابراین تبدیل قابل مشاهده باقی می‌ماند. در مقابل، عرض واقعی رندر شده جعبه، نتیجه محدود کردن آن مقدار `vw` بین دو حد پیکسلی است و می‌تواند تفاوت قابل توجهی با خود `value` داشته باشد – برای مثال، زمانی که لغزنده ترجیحی به زیر لغزنده پایین یا بالای لغزنده بالا کشیده شود.

#### HTML

ابتدا یک عنصر {{htmlelement("div")}} برای جعبه قابل تغییر اندازه، سه لغزنده برای تنظیم مقادیر حداقل، ترجیحی و حداکثر عرض آن، و عناصر {{htmlelement("output")}} برای نمایش عددی مقادیر لغزنده تعریف می‌کنیم. هر سه لغزنده محدوده یکسان ۰ تا ۴۰۰ پیکسل را به اشتراک می‌گذارند، بنابراین موقعیت‌های آنها مستقیماً قابل مقایسه است. مقادیر اولیه را طوری تنظیم می‌کنیم که `lower < pref < upper` باشد.

```html
<div id="box"></div>
<div class="controls">
  <label for="lower">Lower (px)</label>
  <input id="lower" type="range" min="0" max="400" value="50" />
  <output for="lower" id="lowerOut"></output>

  <label for="pref">Preferred (px)</label>
  <input id="pref" type="range" min="0" max="400" value="180" />
  <output for="pref" id="prefOut"></output>

  <label for="upper">Upper (px)</label>
  <input id="upper" type="range" min="0" max="400" value="350" />
  <output for="upper" id="upperOut"></output>
</div>
<pre id="log"></pre>
```

در انتها یک عنصر `#log` برای خروجی اطلاعات بازگردانده‌شده در مورد عرض جعبه تعریف کرده‌ایم.

#### CSS

CSS ویژگی‌های بصری و تراز جعبه، لغزنده‌ها و سایر عناصر را تنظیم می‌کند.

```css
#box {
  height: 50px;
  background: rebeccapurple;
}

.controls {
  display: grid;
  grid-template-columns: auto 1fr auto;
  align-items: center;
  gap: 0.5rem 1rem;
  max-width: 400px;
}

.controls output {
  font-family: monospace;
  text-align: right;
}
```

```css hidden
#log {
  height: 100px;
  overflow: scroll;
  padding: 0.5rem;
  border: 1px solid black;
}
```

#### JavaScript

ابتدا متغیرهایی برای ارجاع به جعبه، لغزنده‌ها و عناصر خروجی ایجاد می‌کنیم.

```js
const box = document.querySelector("#box");
const lowerInput = document.querySelector("#lower");
const prefInput = document.querySelector("#pref");
const upperInput = document.querySelector("#upper");
const lowerOut = document.querySelector("#lowerOut");
const prefOut = document.querySelector("#prefOut");
const upperOut = document.querySelector("#upperOut");
```

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText += `${text}\n`;
}
```

سپس تابع `update()` را برای به‌روزرسانی جعبه و عناصر خروجی بر اساس مقدار لغزنده فراخوانی می‌کنیم. یک شنونده تنظیم می‌کنیم تا تابع هر زمان که موقعیت لغزنده‌ها تغییر کرد، فراخوانی شود.

```js
[lowerInput, prefInput, upperInput].forEach((el) =>
  el.addEventListener("input", update),
);
update();
```

تابع `update()` در زیر نشان داده شده است. این تابع مقادیر لغزنده‌ها را ثبت می‌کند و از آنها هنگام ایجاد یک `CSSMathClamp` استفاده می‌کند که سپس روی ویژگی `width` جعبه تنظیم می‌شود. سپس سبک‌های ویژگی جعبه با استفاده از {{domxref("HTMLElement.attributeStyleMap")}} خوانده می‌شوند و مقادیر بازیابی‌شده `width` نیز به همراه عرض رندر شده جعبه ثبت می‌شوند.

یک پیچیدگی در کد این است که در حالی که `lower` و `upper` به عنوان پیکسل به سازنده `CSSMathClamp()` ارسال می‌شوند و دقیقاً با لغزنده‌های خود مطابقت دارند، مقدار پیکسلی `preferred` ابتدا به واحد `vw` (عرض viewport) تبدیل می‌شود. این کار به این دلیل انجام شده است که اگر هر سه عملوند طول‌های مطلق بودند (مثلاً همه بر حسب پیکسل)، مرورگر می‌توانست `clamp()` را به یک عدد ثابت واحد کاهش دهد، که به جای یک `CSSMathClamp` به صورت یک {{domxref("CSSUnitValue")}} بازخوانی می‌شد. تبدیل `preferred` به یک واحد نسبی مانند `vw` به این معنی است که مرورگر نمی‌تواند عبارت را تا زمان چیدمان حل کند، بنابراین مقدار را به عنوان یک `CSSMathClamp` زنده با هر سه عملوند دست نخورده نگه می‌دارد.

```js
function update() {
  logElement.innerText = "";

  // The preferred slider uses the same 0-400px scale as lower and upper,
  // so its value is converted to vw before being passed to CSSMathClamp.
  const prefVw = (prefInput.value / window.innerWidth) * 100;
  lowerOut.textContent = `${lowerInput.value}px`;
  prefOut.textContent = `${prefInput.value}px (~${prefVw.toFixed(1)}vw)`;
  upperOut.textContent = `${upperInput.value}px`;

  try {
    const clampValue = new CSSMathClamp(
      CSS.px(lowerInput.value),
      CSS.vw(prefVw),
      CSS.px(upperInput.value),
    );
    box.attributeStyleMap.set("width", clampValue);
    const widthClamp = box.attributeStyleMap.get("width");
    const valuePx = (widthClamp.value.value / 100) * window.innerWidth;
    log(`type: ${widthClamp.constructor.name}`);
    log(`lower: ${widthClamp.lower}`);
    log(`value: ${widthClamp.value} (~${valuePx.toFixed(1)}px)`);
    log(`upper: ${widthClamp.upper}`);
    log(`rendered width: ${getComputedStyle(box).width}`);
  } catch (e) {
    log(`Error: ${e.message}`);
  }
}
```

#### نتیجه

لغزنده‌ها را بکشید تا ببینید چگونه `lower`، `value` و `upper` همیشه با موقعیت لغزنده‌ها مطابقت دارند، در حالی که عرض رندر شده بین `lower` و `upper` محدود می‌شود.

{{EmbedLiveSample("Inspecting a clamped value", 300, 350)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CSSMathMax")}}
- {{domxref("CSSMathMin")}}
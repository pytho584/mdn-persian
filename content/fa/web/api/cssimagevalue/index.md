---
title: CSSImageValue
slug: Web/API/CSSImageValue
page-type: web-api-interface
browser-compat: api.CSSImageValue
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

رابط **`CSSImageValue`** در [مدل شیء تایپ‌شده CSS](/en-US/docs/Web/API/CSS_Typed_OM_API) مقادیر مربوط به ویژگی‌های CSS را که یک مقدار {{cssxref("image")}} می‌پذیرند، مانند {{cssxref("background-image")}}، {{cssxref("list-style-image")}} یا {{cssxref("border-image-source")}}، نمایش می‌دهد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

هیچ‌کدام.

## روش‌های نمونه

_همچنین روش‌های رابط والد خود، {{DOMxRef("CSSStyleValue")}} را به ارث می‌برد._

## توضیحات

`CSSImageValue` می‌تواند هر نوع مقداری را که نوع داده {{cssxref("image")}} می‌پذیرد، شامل شود: تصاویر مبتنی بر URL که با {{cssxref("url_function", "url()")}} مشخص می‌شوند، {{cssxref("gradient")}}هایی مانند {{cssxref("gradient/linear-gradient", "linear-gradient()")}}، {{cssxref("image/image", "image()")}}، {{cssxref("image/image-set", "image-set()")}}، {{cssxref("cross-fade", "cross-fade()")}} و {{cssxref("element()")}}.

برای مقادیر تصویری که شامل URL هستند، مانند `url()` یا `image()`، URLهای نسبی و قطعه‌ای (fragment) به همان روشی که در CSS انجام می‌شود، تفسیر می‌شوند. یعنی نسبت به URL برگه سبک (stylesheet) یا URL سند برای سبک‌های درون‌خطی (inline styles).

این تفسیر در زمان محاسبه مقدار (value computation) انجام می‌شود، نه در زمان تجزیه (parse time)، به این معنی که مقدار یک `CSSImageValue` بستگی به این دارد که با مقدار مشخص‌شده (specified value) کار می‌کنید یا مقدار محاسبه‌شده (computed value):

- یک مقدار **مشخص‌شده** یک URL نسبی تفسیرنشده را حمل می‌کند. اگر این مقدار تفسیرنشده به عنصری در سندی دیگر کپی شود، نسبت به URL پایه سند مقصد تفسیر می‌شود و ممکن است به منبع متفاوتی اشاره کند.
- یک مقدار **محاسبه‌شده** قبلاً به یک URL مطلق تفسیر شده است، بنابراین صرف‌نظر از اینکه بعداً به کدام سند اعمال شود، رفتار یکسانی دارد.
- یک مقدار URL **فقط-قطعه‌ای** همیشه نسبت به سند جاری تفسیر می‌شود.

توجه داشته باشید که اشیاء `CSSImageValue` عمداً مبهم هستند: هیچ اطلاعاتی درباره تصویری که نمایش می‌دهند فاش نمی‌کنند.

## مثال‌ها

### استفاده پایه

این مثال `background-image` یک {{htmlelement("button")}} را با استفاده از `url()` و یک URL نسبی برای فایل تنظیم می‌کند. سپس مقادیر محاسبه‌شده و مشخص‌شده را به صورت رشته‌ای (stringified) دریافت می‌کنیم.

توجه داشته باشید که کد ثبت لاگ (logging) پنهان وجود دارد که در اینجا نمایش داده نمی‌شود، زیرا به مثال مربوط نیست.

#### HTML

ابتدا عنصر دکمه را تعریف می‌کنیم:

```html
<button>Magic Wand</button>
```

```html hidden
<pre id="log"></pre>
```

#### CSS

مقداری CSS اضافه می‌کنیم، از جمله یک تصویر پس‌زمینه که یک فایل باینری را درخواست می‌کند:

```css
button {
  display: inline-block;
  min-height: 100px;
  min-width: 100px;
  background: no-repeat 5% center url("magic-wand.png") aqua;
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

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

سپس عنصر `<button>` را دریافت می‌کنیم تا بتوانیم سبک‌های مشخص‌شده و محاسبه‌شده آن را پرس‌وجو کنیم.

```js
// get the element
const button = document.querySelector("button");
```

برای دریافت مقدار محاسبه‌شده `background-image` ابتدا نقشه سبک (style map) عنصر را با `computedStyleMap()` به دست می‌آوریم. سپس `background-image` را از نقشه سبک با `get()` دریافت کرده و به صورت رشته درمی‌آوریم. همچنین نام سازنده (constructor) را چاپ می‌کنیم تا نشان دهیم که شیء برگشتی یک `CSSImageValue` است.

```js
// Get all computed styles with computedStyleMap()
const allComputedStyles = button.computedStyleMap();
const computedImageCSS = allComputedStyles.get("background-image");
log(computedImageCSS.toString());
log(computedImageCSS.constructor.name); // CSSImageValue
```

در مرحله بعد مقدار مشخص‌شده `background-image` را دریافت می‌کنیم. برای این کار ابتدا مجموعه قوانین CSS مرتبط با عنصر `css-output` را به دست می‌آوریم – این جایی است که MDN CSS را برای محیط آزمایشی (playground) می‌نویسد. سپس قانونی را فیلتر می‌کنیم که با نام "button" مطابقت دارد (توجه داشته باشید که این کد در یک برنامه واقعی شکننده است). پس از به دست آوردن قانون مرتبط، می‌توانیم تصویر را از نقشه سبک آن دریافت کرده و مقدار را لاگ کنیم.

```js
// Get the specified value
const sheet = document.getElementById("css-output").sheet;
const rule = [...sheet.cssRules].find((r) => r.selectorText === "button");
const specifiedImageCSS = rule.styleMap.get("background-image");
log(specifiedImageCSS.toString());
log(specifiedImageCSS.constructor.name); // CSSImageValue
```

#### نتیجه

نتایج در زیر نمایش داده شده‌اند. توجه داشته باشید که مقدار محاسبه‌شده که ابتدا نمایش داده می‌شود یک URL کاملاً تفسیرشده دارد، در حالی که مقدار مشخص‌شده یک URL نسبی است.

{{EmbedLiveSample("Examples", 120, 300)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CSSKeywordValue")}}
- {{domxref("CSSNumericValue")}}
- {{domxref("CSSPositionValue")}}
- {{domxref("CSSTransformValue")}}
- {{domxref("CSSUnparsedValue")}}
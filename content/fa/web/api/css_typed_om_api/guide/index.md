---
title: "Using the CSS Typed Object Model"
slug: Web/API/CSS_Typed_OM_API/Guide
page-type: guide
---

{{DefaultAPISidebar("CSS Typed Object Model API")}}

**CSS Typed Object Model API** (مدل شیء تایپ‌شده CSS) مقادیر CSS را به عنوان اشیاء تایپ‌شده جاوااسکریپت در معرض دید قرار می‌دهد تا امکان دستکاری کارآمد آن‌ها فراهم شود.

تبدیل رشته‌های مقدار [CSS Object Model](/en-US/docs/Web/API/CSS_Object_Model) به نمایش‌های جاوااسکریپتی با نوع‌معنی و برگشت (از طریق {{domxref("HTMLElement.style")}}) می‌تواند سربار عملکرد قابل توجهی ایجاد کند.

CSS Typed OM با ارائه ویژگی‌های شیء (به جای دستکاری رشته‌ای CSSOM)، دسترسی به انواع، روش‌ها و یک مدل شیء برای مقادیر CSS، دستکاری CSS را منطقی‌تر و کارآمدتر می‌کند.

این مقاله مقدمه‌ای بر تمام ویژگی‌های اصلی آن ارائه می‌دهد.

## computedStyleMap()

با CSS Typed OM API، می‌توانیم به تمام ویژگی‌ها و مقادیر CSS – از جمله ویژگی‌های سفارشی – که بر یک عنصر تأثیر می‌گذارند دسترسی داشته باشیم. بیایید با ایجاد اولین مثال خود که {{domxref('Element.computedStyleMap()', 'computedStyleMap()')}} را بررسی می‌کند، نحوه کار این را ببینیم.

### دریافت تمام ویژگی‌ها و مقادیر

#### HTML

با مقداری HTML شروع می‌کنیم: یک پاراگراف با یک پیوند، و همچنین یک لیست تعریف که تمام جفت‌های ویژگی/مقدار CSS را به آن اضافه خواهیم کرد.

```html
<p>
  <a href="https://example.com">Link</a>
</p>
<dl id="regurgitation"></dl>
```

#### JavaScript

جاوااسکریپت را اضافه می‌کنیم تا پیوند بدون استایل خود را بگیرد و با استفاده از `computedStyleMap()` یک لیست تعریف از تمام مقادیر ویژگی CSS پیش‌فرض که بر پیوند تأثیر می‌گذارند، برگرداند.

```js
// Get the element
const myElement = document.querySelector("a");

// Get the <dl> we'll be populating
const stylesList = document.querySelector("#regurgitation");

// Retrieve all computed styles with computedStyleMap()
const defaultComputedStyles = myElement.computedStyleMap();

// Iterate through the map of all the properties and values, adding a <dt> and <dd> for each
for (const [prop, val] of defaultComputedStyles) {
  // properties
  const cssProperty = document.createElement("dt");
  cssProperty.appendChild(document.createTextNode(prop));
  stylesList.appendChild(cssProperty);

  // values
  const cssValue = document.createElement("dd");
  cssValue.appendChild(document.createTextNode(val));
  stylesList.appendChild(cssValue);
}
```

متد `computedStyleMap()` یک شیء {{domxref('StylePropertyMapReadOnly')}} حاوی ویژگی [`size`](/en-US/docs/Web/API/StylePropertyMapReadOnly/size) برمی‌گرداند که نشان می‌دهد چند ویژگی در نقشه وجود دارد. ما درون نقشه استایل تکرار می‌کنیم و به ترتیب برای هر ویژگی و مقدار یک [`<dt>`](/en-US/docs/Web/HTML/Reference/Elements/dt) و [`<dd>`](/en-US/docs/Web/HTML/Reference/Elements/dd) ایجاد می‌کنیم.

#### نتیجه

در [مرورگرهایی که از `computedStyleMap()` پشتیبانی می‌کنند](/en-US/docs/Web/API/Element/computedStyleMap#browser_compatibility)، لیستی از تمام ویژگی‌ها و مقادیر CSS را خواهید دید. در سایر مرورگرها، فقط یک پیوند را مشاهده می‌کنید.

{{EmbedLiveSample("Getting_all_the_properties_and_values", 120, 300)}}

آیا متوجه شدید که یک پیوند چند ویژگی پیش‌فرض CSS دارد؟ اولین فراخوانی `document.querySelector` را به انتخاب {{htmlelement("p")}} به جای {{htmlelement("a")}} تغییر دهید. در مقادیر محاسبه‌شده پیش‌فرض {{cssxref("margin-top")}} و {{cssxref("margin-bottom")}} تفاوت را مشاهده خواهید کرد.

### متد .get() / ویژگی‌های سفارشی

بیایید مثال خود را به‌روزرسانی کنیم تا فقط چند ویژگی و مقدار را بازیابی کنیم. ابتدا مقداری CSS به مثال خود اضافه می‌کنیم، از جمله یک ویژگی سفارشی و یک ویژگی قابل ارث‌بری:

```css
p {
  font-weight: bold;
}

a {
  --color: red;
  color: var(--color);
}
```

به جای دریافت _همه_ ویژگی‌ها، یک آرایه از ویژگی‌های مورد نظر ایجاد کرده و از متد {{domxref('StylePropertyMapReadOnly.get()')}} برای دریافت هر یک از مقادیر آن‌ها استفاده می‌کنیم:

```html hidden
<p>
  <a href="https://example.com">Link</a>
</p>
<dl id="regurgitation"></dl>
```

```js
// Get the element
const myElement = document.querySelector("a");

// Get the <dl> we'll be populating
const stylesList = document.querySelector("#regurgitation");

// Retrieve all computed styles with computedStyleMap()
const allComputedStyles = myElement.computedStyleMap();

// Array of properties we're interested in
const ofInterest = ["font-weight", "border-left-color", "color", "--color"];

// iterate through our properties of interest
for (const value of ofInterest) {
  // Properties
  const cssProperty = document.createElement("dt");
  cssProperty.appendChild(document.createTextNode(value));
  stylesList.appendChild(cssProperty);

  // Values
  const cssValue = document.createElement("dd");
  cssValue.appendChild(document.createTextNode(allComputedStyles.get(value)));
  stylesList.appendChild(cssValue);
}
```

{{EmbedLiveSample(".get_method_custom_properties", 120, 300)}}

ما {{cssxref('border-left-color')}} را گنجانده‌ایم تا نشان دهیم که اگر همه ویژگی‌ها را شامل می‌شدیم، هر مقداری که به طور پیش‌فرض [`currentColor`](/en-US/docs/Web/CSS/Reference/Values/color_value) است (از جمله {{cssxref('caret-color')}}، {{cssxref('outline-color')}}، {{cssxref('text-decoration-color')}}، {{cssxref('column-rule-color')}} و غیره) `rgb(255 0 0)` را برمی‌گرداند. پیوند `font-weight: bold;` را از استایل‌های پاراگراف به ارث برده است که به صورت `font-weight: 700` فهرست شده است. ویژگی‌های سفارشی، مانند `--color: red` ما، ویژگی هستند. بنابراین، از طریق `get()` قابل دسترسی هستند.

توجه خواهید کرد که ویژگی‌های سفارشی مقدار را همانطور که در شیوه‌نامه نوشته شده حفظ می‌کنند، در حالی که استایل‌های محاسبه‌شده به عنوان مقدار محاسبه‌شده فهرست می‌شوند – {{cssxref('color')}} به عنوان یک مقدار [`rgb()`](/en-US/docs/Web/CSS/Reference/Values/color_value) و {{cssxref('font-weight')}} برگشتی `700` بود، حتی اگر ما از یک [رنگ نام‌گذاری‌شده](/en-US/docs/Web/CSS/Reference/Values/named-color) و کلیدواژه `bold` استفاده می‌کنیم.

### CSSUnitValue و CSSKeywordValue

قدرت CSS Typed OM در این است که مقادیر از واحدها جدا هستند؛ تجزیه و الحاق رشته‌های مقدار ممکن است به گذشته تبدیل شود. هر ویژگی CSS در یک نقشه استایل یک مقدار دارد. اگر مقدار یک کلیدواژه باشد، شیء برگشتی یک [`CSSKeywordValue`](/en-US/docs/Web/API/CSSKeywordValue) است. اگر مقدار عددی باشد، یک [`CSSUnitValue`](/en-US/docs/Web/API/CSSUnitValue) برگردانده می‌شود.

`CSSKeywordValue` کلاسی است که کلیدواژه‌هایی مانند `inherit`، `initial`، `unset` و سایر رشته‌هایی که نقل قول نمی‌شوند، مانند `auto` و `grid` را تعریف می‌کند. این زیرکلاس یک ویژگی `value` از طریق {{domxref("cssKeywordValue.value")}} به شما می‌دهد.

`CSSUnitValue` در صورتی برگردانده می‌شود که مقدار از نوع واحد باشد. این کلاسی است که اعداد با واحدهای اندازه‌گیری مانند `20px`، `40%`، `200ms` یا `7` را تعریف می‌کند. با دو ویژگی `value` و `unit` برگردانده می‌شود. با این نوع می‌توانیم به مقدار عددی – {{domxref('cssUnitValue.value')}} – و واحد آن – {{domxref('cssUnitValue.unit')}} – دسترسی داشته باشیم.

بیایید یک پاراگراف ساده بنویسیم، هیچ استایلی اعمال نکنیم و با برگرداندن یک جدول با واحد و مقدار، چند ویژگی CSS آن را بررسی کنیم:

```html
<p>
  This is a paragraph with some content. Open up this example in CodePen or
  JSFiddle, and change some features. Try adding some CSS, such as a width for
  this paragraph, or adding a CSS property to the ofInterest array.
</p>
<table id="regurgitation">
  <thead>
    <tr>
      <th>Property</th>
      <th>Value</th>
      <th>Unit</th>
    </tr>
  </thead>
</table>
```

برای هر ویژگی مورد نظر، نام ویژگی را فهرست می‌کنیم، از `.get(propertyName).value` برای برگرداندن مقدار استفاده می‌کنیم، و اگر شیء برگشتی توسط `get()` یک `CSSUnitValue` باشد، نوع واحدی را که با `.get(propertyName).unit` بازیابی می‌کنیم فهرست می‌کنیم.

```js
// Get the element we're inspecting
const myElement = document.querySelector("p");

// Get the table we'll be populating
const stylesTable = document.querySelector("#regurgitation");

// Retrieve all computed styles with computedStyleMap()
const allComputedStyles = myElement.computedStyleMap();

// Array of properties we're interested in
const ofInterest = [
  "padding-top",
  "margin-bottom",
  "font-size",
  "font-stretch",
  "animation-duration",
  "animation-iteration-count",
  "width",
  "height",
];

// Iterate through our properties of interest
for (const value of ofInterest) {
  // Create a row
  const row = document.createElement("tr");

  // Add the name of the property
  const cssProperty = document.createElement("td");
  cssProperty.appendChild(document.createTextNode(value));
  row.appendChild(cssProperty);

  // Add the unitless value
  const cssValue = document.createElement("td");

  // Shrink long floats to 1 decimal point
  let propVal = allComputedStyles.get(value).value;
  propVal = propVal % 1 ? propVal.toFixed(1) : propVal;
  cssValue.appendChild(document.createTextNode(propVal));
  row.appendChild(cssValue);

  // Add the type of unit
  const cssUnit = document.createElement("td");
  cssUnit.appendChild(
    document.createTextNode(allComputedStyles.get(value).unit),
  );
  row.appendChild(cssUnit);

  // Add the row to the table
  stylesTable.appendChild(row);
}
```

{{EmbedLiveSample("CSSUnitValue_and_CSSKeywordValue", 120, 300)}}

برای کسانی که از مرورگر غیرپشتیبان استفاده می‌کنند، خروجی بالا باید چیزی شبیه به این باشد:

| Property                                 | Value | Unit        |
| ---------------------------------------- | ----- | ----------- |
| {{cssxref("padding-top")}}               | 0     | `px`        |
| {{cssxref("margin-bottom")}}             | 16    | `px`        |
| {{cssxref("font-size")}}                 | 16    | `px`        |
| {{cssxref("font-stretch")}}              | 100   | `%`         |
| {{cssxref("animation-duration")}}        | 0     | `px`        |
| {{cssxref("animation-iteration-count")}} | 1     | _number_    |
| {{cssxref("width")}}                     | auto  | _undefined_ |
| {{cssxref("height")}}                    | auto  | _undefined_ |

توجه خواهید کرد که واحد {{cssxref('&lt;length&gt;')}} بازگشتی `px` است، واحد {{cssxref('&lt;percentage&gt;')}} بازگشتی `percent` است، واحد {{cssxref('&lt;time&gt;')}} برای 'ثانیه' `s` است، و واحد بدون عدد {{cssxref('&lt;number&gt;')}} `number` است.

ما برای پاراگراف {{cssxref('width')}} یا {{cssxref('height')}} اعلام نکردیم، که هر دو به طور پیش‌فرض `auto` هستند و بنابراین به جای [`CSSUnitValue`](/en-US/docs/Web/API/CSSUnitValue) یک [`CSSKeywordValue`](/en-US/docs/Web/API/CSSKeywordValue) برمی‌گردانند. `CSSKeywordValue`ها ویژگی unit ندارند، بنابراین در این موارد `get().unit` ما `undefined` برمی‌گرداند.

اگر `width` یا `height` در یک `<length>` یا `<percent>` تعریف شده بود، واحد [`CSSUnitValue`](/en-US/docs/Web/API/CSSUnitValue) به ترتیب `px` یا `percent` بود.

انواع دیگری نیز موجود است:

- یک {{cssxref("image")}} یک {{domxref('CSSImageValue')}} برمی‌گرداند.
- یک {{cssxref("&lt;color&gt;")}} یک {{domxref('CSSStyleValue')}} برمی‌گرداند.
- یک {{cssxref('transform')}} یک `CSSTransformValue` برمی‌گرداند.
- یک [ویژگی سفارشی](/en-US/docs/Web/CSS/Reference/Properties/--*) یک {{domxref('CSSUnparsedValue')}} برمی‌گرداند.

می‌توانید از یک `CSSUnitValue` یا `CSSKeywordValue` برای ایجاد اشیاء دیگر استفاده کنید.

## CSSStyleValue

رابط `CSSStyleValue` از [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Object_Model#css_typed_object_model) کلاس پایه همه مقادیر CSS قابل دسترسی از طریق Typed OM API است، از جمله {{domxref('CSSImageValue')}}، {{domxref('CSSKeywordValue')}}، {{domxref('CSSNumericValue')}}، {{domxref('CSSPositionValue')}}، {{domxref('CSSTransformValue')}} و {{domxref('CSSUnparsedValue')}}.

دارای دو روش است:

- {{domxref("CSSStyleValue/parse_static", "CSSStyleValue.parse()")}}
- {{domxref("CSSStyleValue/parseAll_static", "CSSStyleValue.parseAll()")}}

همانطور که در بالا ذکر شد، `StylePropertyMapReadOnly.get('--customProperty')` یک {{domxref('CSSUnparsedValue')}} برمی‌گرداند. ما می‌توانیم نمونه‌های شیء `CSSUnparsedValue` را با روش‌های به ارث‌رسیده {{domxref('CSSStyleValue/parse_static', 'CSSStyleValue.parse()')}} و {{domxref('CSSStyleValue/parseAll_static', 'CSSStyleValue.parseAll()')}} تجزیه کنیم.

بیایید یک مثال CSS با چندین ویژگی سفارشی، تبدیل‌ها، `calc()`ها و ویژگی‌های دیگر را بررسی کنیم. با استفاده از قطعه‌های کوتاه جاوااسکریپت که به {{domxref("console/log_static", "console.log()")}} خروجی می‌دهند، به نوع آن‌ها نگاه خواهیم کرد:

```css
:root {
  --main-color: hsl(198 43% 42%);
  --black: hsl(0 0% 16%);
  --white: hsl(0 0% 97%);
  --unit: 1.2rem;
}

button {
  --main-color: hsl(198 100% 66%);
  display: inline-block;
  padding: var(--unit) calc(var(--unit) * 2);
  width: calc(30% + 20px);
  background: no-repeat 5% center url("magic-wand.png") var(--main-color);
  border: 4px solid var(--main-color);
  border-radius: 2px;
  font-size: calc(var(--unit) * 2);
  color: var(--white);
  cursor: pointer;
  transform: scale(0.95);
}
```

بیایید کلاس را به یک دکمه اضافه کنیم (دکمه‌ای که هیچ کاری انجام نمی‌دهد).

```html
<button>Styled Button</button>
```

```html hidden
<p>
  There is nothing to see here. Please open your browser console to see the
  output!
</p>
```

ما `StylePropertyMapReadOnly` خود را با جاوااسکریپت زیر می‌گیریم:

```js
const allComputedStyles = document.querySelector("button").computedStyleMap();
```

مثال‌های زیر به `allComputedStyles` اشاره دارند:

### CSSUnparsedValue

{{domxref('CSSUnparsedValue')}} نمایانگر [ویژگی‌های سفارشی](/en-US/docs/Web/CSS/Guides/Cascading_variables/Using_custom_properties) است:

```js
// CSSUnparsedValue
const unit = allComputedStyles.get("--unit");

console.log(unit); // CSSUnparsedValue {0: " 1.2rem", length: 1}
console.log(unit[0]); // " 1.2rem"
```

هنگامی که `get()` را فراخوانی می‌کنیم، یک ویژگی سفارشی از نوع `CSSUnparsedValue` برگردانده می‌شود. به فاصله قبل از `1.2rem` توجه کنید. برای به دست آوردن یک واحد و مقدار، به یک `CSSUnitValue` نیاز داریم که می‌توانیم با استفاده از روش `CSSStyleValue.parse()` روی `CSSUnparsedValue` آن را بازیابی کنیم.

```js
const parsedUnit = CSSNumericValue.parse(unit);
console.log(parsedUnit); // CSSUnitValue {value: 1.2, unit: "rem"}
console.log(parsedUnit.unit); // "rem"
console.log(parsedUnit.value); // 1.2
```

### CSSMathSum

اگرچه عنصر [`<button>`](/en-US/docs/Web/HTML/Reference/Elements/button) به طور پیش‌فرض یک عنصر درون‌خطی است، ما [`display: inline-block;`](/en-US/docs/Web/CSS/Guides/Display) را برای فعال‌سازی اندازه‌دهی اضافه کرده‌ایم. در CSS ما `width: calc(30% + 20px);` داریم که یک تابع {{cssxref("calc()")}} برای تعریف عرض است.

هنگامی که `width` را `get()` می‌کنیم، یک [`CSSMathSum`](/en-US/docs/Web/API/CSSMathSum) برگردانده می‌شود. {{domxref('CSSMathSum.values')}} یک {{domxref('CSSNumericArray')}} با 2 `CSSUnitValue` است.

مقدار {{domxref('CSSMathValue.operator')}} `sum` است:

```js
const btnWidth = allComputedStyles.get("width");

console.log(btnWidth); // CSSMathSum
console.log(btnWidth.values); // CSSNumericArray {0: CSSUnitValue, 1: CSSUnitValue, length: 2}
console.log(btnWidth.operator); // 'sum'
```

### CSSTransformValue با CSSScale

[`display: inline-block;`](/en-US/docs/Web/CSS/Guides/Display) همچنین تبدیل را فعال می‌کند. در CSS ما `transform: scale(0.95);` داریم که یک تابع {{cssxref('transform')}} است.

```js
const transform = allComputedStyles.get("transform");

console.log(transform); // CSSTransformValue {0: CSSScale, 1: CSSTranslate, length: 2, is2D: true}
console.log(transform.length); // 1
console.log(transform[0]); // CSSScale {x: CSSUnitValue, y: CSSUnitValue, z: CSSUnitValue, is2D: true}
console.log(transform[0].x); // CSSUnitValue {value: 0.95, unit: "number"}
console.log(transform[0].y); // CSSUnitValue {value: 0.95, unit: "number"}
console.log(transform[0].z); // CSSUnitValue {value: 1, unit: "number"}
console.log(transform.is2D); // true
```

هنگامی که ویژگی `transform` را `get()` می‌کنیم، یک {{domxref('CSSTransformValue')}} دریافت می‌کنیم. می‌توانیم طول (یا تعداد) توابع تبدیل را با ویژگی `length` پرس‌وجو کنیم.

از آنجایی که طول `1` داریم که نشان‌دهنده یک تابع تبدیل واحد است، اولین شیء را ثبت می‌کنیم و یک شیء `CSSScale` دریافت می‌کنیم. هنگامی که `x`، `y` و `z` مقیاس‌بندی را پرس‌وجو می‌کنیم، `CSSUnitValue` دریافت می‌کنیم. ویژگی فقط‌خواندنی `CSSScale.is2D` در این سناریو `true` است.

اگر توابع تبدیل `translate()`، `skew()` و `rotate()` را اضافه کرده بودیم، طول `4` بود، هر کدام با مقادیر `x`، `y`، `z` خود و هر کدام با یک ویژگی `.is2D`. به عنوان مثال، اگر `transform: translate3d(1px, 1px, 3px)` را گنجانده بودیم، `.get('transform')` یک `CSSTranslate` با `CSSUnitValues` برای `x`، `y` و `z` برمی‌گرداند و ویژگی فقط‌خواندنی `.is2D` `false` بود.

### CSSImageValue

دکمه ما یک تصویر پس‌زمینه دارد: یک عصای جادویی.

```js
const bgImage = allComputedStyles.get("background-image");

console.log(bgImage); // CSSImageValue
console.log(bgImage.toString()); // url("magic-wand.png")
```

هنگامی که `'background-image'` را `get()` می‌کنیم، یک {{domxref('CSSImageValue')}} برگردانده می‌شود. در حالی که ما از ویژگی کوتاه‌نویس {{cssxref('background')}} CSS استفاده کرده‌ایم، روش به ارث‌رسیده {{jsxref("Object/toString", "Object.prototype.toString()")}} نشان می‌دهد که ما فقط تصویر، `'url("magic-wand.png")'` را برگردانده‌ایم.

توجه داشته باشید که مقدار برگشتی مسیر مطلق تصویر است – این حتی اگر مقدار اصلی `url()` نسبی بوده باشد، برگردانده می‌شود. اگر تصویر پس‌زمینه یک گرادیان یا چندین تصویر پس‌زمینه بود، `.get('background-image')` یک `CSSStyleValue` برمی‌گرداند. `CSSImageValue` فقط در صورتی برگردانده می‌شود که یک تصویر واحد وجود داشته باشد و فقط اگر آن اعلام تصویر واحد یک URL باشد.

در نهایت، همه اینها را در یک نمونه زنده کنار هم قرار می‌دهیم. برای بازرسی خروجی، از کنسول مرورگر خود استفاده کنید.

{{EmbedLiveSample("CSSStyleValue", 120, 300)}}

## خلاصه

این باید شما را برای درک CSS Typed OM شروع کند. برای کسب اطلاعات بیشتر به تمام [رابط‌های CSS Typed OM](/en-US/docs/Web/API/CSS_Typed_OM_API) نگاهی بیندازید.

## همچنین ببینید

- [استفاده از CSS Painting API](/en-US/docs/Web/API/CSS_Painting_API/Guide)
---
title: CSSStyleProperties
slug: Web/API/CSSStyleProperties
page-type: web-api-interface
browser-compat: api.CSSStyleProperties
---

{{APIRef("CSSOM")}}

رابطهٔ **`CSSStyleProperties`** در [مدل شیءگرای CSS (CSSOM)](/en-US/docs/Web/API/CSS_Object_Model) سبکهای درونخطی (inline) یا محاسبهایِ موجود روی یک عنصر، یا سبکهای مرتبط با یک قانون استایل CSS را نمایش میدهد.

{{InheritanceDiagram}}

## ویژگیهای نمونه

_این رابط همچنین ویژگیهای والد خود، {{domxref("CSSStyleDeclaration")}} را به ارث میبرد._

- ویژگیهای نامدار
  - : ویژگیهای نامدار با خط تیره و نام驼峰 (camel-case) برای تمام ویژگیهای CSS که مرورگر از آنها پشتیبانی میکند.
- {{DOMxRef("CSSStyleProperties.cssFloat", "CSStyleProperties.cssFloat")}}
  - : نام مستعار ویژه برای ویژگی CSS {{CSSxRef("float")}}.

## روشهای نمونه

_این رابط روشهای والد خود، {{domxref("CSSStyleDeclaration")}} را به ارث میبرد._

## توضیحات

یک شیء از این نوع دارای ویژگیهای نامدار با خط تیره برای **همه** [ویژگیهای CSS](/en-US/docs/Web/CSS/Reference/Properties) است که مرورگر از آنها پشتیبانی میکند، از جمله ویژگیهای [کوتاهنوشت (shorthand)](/en-US/docs/Web/CSS/Guides/Cascade/Shorthand_properties) و بلندنوشت (longhand)، و همچنین آنهایی که پیشوند `-moz` و `-webkit` دارند.
این ویژگیها را میتوان با استفاده از روشهای به ارث رسیده از کلاس پایهٔ {{DOMxRef("CSSStyleDeclaration")}}، مانند {{DOMxRef("CSSStyleDeclaration/getPropertyValue", "getPropertyValue()")}} و {{DOMxRef("CSSStyleDeclaration/setProperty", "setProperty()")}} مورد دسترسی قرار داد.

علاوه بر این، هر ویژگی با نام خط تیرهدار، دارای یک ویژگی متناظر با نام {{glossary("camel case")}} است که نام آن با حذف خط تیرهها و بزرگکردن حرف اول هر کلمه بعد از کلمهٔ اول ساخته میشود.
این به شما امکان میدهد برای مثال، به ویژگی CSS «margin-top» با استفاده از نحو `style.marginTop` (جایی که `style` یک `CSSStyleProperties` است) دسترسی پیدا کنید، به جای روش پرمشقتتر `style.getPropertyValue("margin-top")` یا `style["margin-top"]`.
ویژگی CSS «float» که یک کلمهٔ کلیدی رزرو شده در جاوااسکریپت است، با ویژگی `cssFloat` نمایش داده میشود.

ویژگیهای کوتاهنوشت CSS یک عنصر به ویژگیهای بلندنوشت متناظرشان گسترش مییابند.
برای مثال، عنصری با استایل `"border-top: 1px solid black"` در شیء بازگشتی با ویژگیهایی به نامهای {{cssxref("border-top")}} و `borderTop` و همچنین ویژگیهای بلندنوشت متناظر {{cssxref("border-top-color")}} و `borderTopColor`، {{cssxref("border-top-style")}} و `borderTopStyle`، و {{cssxref("border-top-width")}} و `borderTopWidth` نمایش داده میشود.

ویژگیها و صفات بدون مقدار تعریفشده، بهطور پیشفرض رشتهٔ خالی (`""`) هستند.
برای شیءای که یک اعلان استایل درونخطی (نه استایل محاسبهای) را نشان میدهد، این به معنای هر استایلی است که در بلوک اعلان تعریف نشده است.

نمونههای شیء `CSSStyleProperties` از طریق APIهای زیر در دسترس قرار میگیرند:

- {{DOMxRef("HTMLElement.style")}}، {{domxref("SVGElement.style")}} و {{domxref("MathMLElement.style")}}: برای دریافت و تنظیم _استایل درونخطی_ یک عنصر واحد (مثلاً `<div style="…">`) استفاده میشوند.
- {{DOMxRef("Window.getComputedStyle()")}}: برای دریافت استایل محاسبهای (فقطخواندنی) یک عنصر به کار میرود که شامل اثرات هر دو استایل درونخطی و خارجی است.
- {{DOMxRef("CSSStyleRule.style")}}: برای دریافت و تنظیم استایلهای یک قانون استایل ({{DOMxRef("CSSStyleRule")}}) استفاده میشود.

## مثالها

### استفادهٔ پایه

این مثال نشان میدهد که چگونه میتوان استایلهای محلی و محاسبهای عنصر را با استفاده از ویژگیهای نام驼峰 و خط تیرهدار دریافت و تنظیم کرد.

#### HTML

اچتیامال یک {{htmlelement("div")}} با تعدادی استایل تنظیمشده تعریف میکند که داخل یک عنصر دیگر قرار گرفته و `font-weight` را به صورت `bold` تنظیم میکند.

```html
<div style="font-weight: bold;">
  <div style="border-top: 3px solid blue; color: red;margin:5px;" id="elt">
    Div content.
    <br />
    Inner: "border-top: 3px solid blue; color: red;margin:5px;".
    <br />
    Outer: "font-weight: bold;"
  </div>
</div>
```

```html hidden
<pre id="log"></pre>
```

```css hidden
#log {
  height: 140px;
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

ابتدا استایل محلی و محاسبهای را برای عنصر با شناسهٔ `"elt"` دریافت میکنیم.

```js
const element = document.querySelector("#elt");
const elementStyle = element.style;
const computedStyle = window.getComputedStyle(element);
```

سپس ویژگی کوتاهنوشت `borderTop` از `CSSStyleProperties` را با استفاده از نقطهنویسی (dot notation) برای هر دو استایل محلی و محاسبهای دریافت میکنیم.
استفاده از نقطهنویسی با یک ویژگی نام驼峰 سادهترین راه برای دسترسی به هر ویژگی است.

```js
// Get style using dot notation
const elemBorderTop = elementStyle.borderTop;
const compBorderTop = computedStyle.borderTop;

log('Format: Style = "Element" / "Computed"');
log(`"borderTop" = "${elemBorderTop}" / "${compBorderTop}"'`);
```

ما همچنین میتوانیم همان ویژگی را با استفاده از روش {{DOMxRef("CSSStyleDeclaration/getPropertyPriority", "getPropertyValue()")}} یا نماد براکتی دریافت کنیم.

```js
// Get style using dashed-name property value
const elemBorderTop = elementStyle.getPropertyValue("border-top");
const compBorderTop = computedStyle.getPropertyValue("border-top");
log(`"border-top" = "${elemBorderTop}" / "${compBorderTop}"'`);
```

کد زیر هر یک از ویژگیهای بلندنوشتی را که با ویژگی کوتاهنوشت `border-top` متناظرند، با استفاده از نقطهنویسی برای سادگی دریافت میکند.

```js
// Get shorthand properties using dot notation
const elemBorderTopWidth = elementStyle.borderTopWidth;
const compBorderTopWidth = computedStyle.borderTopWidth;
log(`"borderTopWidth" = "${elemBorderTopWidth}" / "${compBorderTopWidth}"'`);

const elemBorderTopColor = elementStyle.borderTopColor;
const compBorderTopColor = computedStyle.borderTopColor;
log(`"borderTopColor" = "${elemBorderTopColor}" / "${compBorderTopColor}"'`);

const elemBorderTopStyle = elementStyle.borderTopStyle;
const compBorderTopStyle = computedStyle.borderTopStyle;
log(`"borderTopStyle" = "${elemBorderTopStyle}" / "${compBorderTopStyle}"'`);

const elemFontWeight = elementStyle.fontWeight;
const compFontWeight = computedStyle.fontWeight;
log(`"fontWeight" = "${elemFontWeight}" / "${compFontWeight}"'`);
```

در نهایت نشان میدهیم که چگونه میتوانید از نقطهنویسی برای تنظیم یک مقدار ویژگی استفاده کنید.
در بخش نتایج زیر متوجه خواهید شد که حاشیهٔ پایینی عنصر یک خط سبز توپر است.

```js
// Set the bottom border style using dot notation
elementStyle.borderBottom = "5px solid green";
```

#### نتایج

نتایج در زیر نشان داده شده است.
توجه کنید که مقادیر ویژگیهای متناظر نام驼峰 (`borderTop`) و خط تیرهدار (`border-top`) یکسان هستند.
مقادیر محلی و محاسبهای برای ویژگیهای بلندنوشت نیز اغلب یکسان هستند، بهجز اینکه ویژگیهای محاسبهای از نحو `rgb()` برای رنگها استفاده میکنند و همچنین سبکهایی را که روی والد `<div>` تنظیم شدهاند، مانند `font-weight`، شامل میشوند.

{{EmbedLiveSample("Basic usage", "100", "250")}}

### شمارش ویژگیهای استایل خط تیرهدار

این مثال نشان میدهد که چگونه میتوان مقادیر ویژگیهای خط تیرهدار یک عنصر را برای هر دو استایل درونخطی و محاسبهای شمارش کرد.

#### HTML

اچتیامال یک {{htmlelement("div")}} با تعدادی استایل تنظیمشده تعریف میکند که داخل عنصر دیگری قرار گرفته و `font-weight` را تنظیم میکند.
همچنین دکمههایی برای دریافت استایلهای درونخطی و محاسبهای عنصر وجود دارد (و کد پنهان برای دکمهٔ بازنشانی و ثبت گزارش).

```html
<div style="font-weight: bold;">
  <div style="border-top: 1px solid blue; color: red;" id="elt">
    An example div
  </div>
</div>
<button id="inline_style" type="button">Inline Style</button>
<button id="computed_style" type="button">Computed Style</button>
```

```html hidden
<button id="reset" type="button">Reset</button>
<pre id="log"></pre>
```

```css hidden
#log {
  height: 300px;
  overflow: scroll;
  padding: 0.5rem;
  border: 1px solid black;
}
```

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}

function clearLog(text) {
  logElement.innerText = "";
}

const reload = document.querySelector("#reset");

reload.addEventListener("click", () => {
  clearLog();
});
```

#### JavaScript

کد ابتدا تابعی را تعریف میکند که برای شمارش ویژگیهای عنصر با شناسهٔ `elt` استفاده میشود.
این تابع از {{domxref("CSSStyleDeclaration.getPropertyValue()")}} برای دریافت مقدار هر ویژگی خط تیرهدار متعلق به شیء که شاخص عددی دارد، استفاده میکند.

```js
function getPopulatedProperties(elementStyles) {
  for (const prop in elementStyles) {
    if (
      // بررسی کنید که ویژگی متعلق به نمونهٔ CSSStyleProperties باشد
      // بررسی کنید که ویژگی شاخص عددی دارد (نشاندهندهٔ استایل درونخطی/خط تیرهدار است)
      Object.hasOwn(elementStyles, prop) &&
      !Number.isNaN(Number.parseInt(prop, 10))
    ) {
      log(
        `${elementStyles[prop]} = '${elementStyles.getPropertyValue(
          elementStyles[prop],
        )}'`,
      );
    }
  }
}
```

کد زیر بررسی و ثبت میکند که آیا `CSSStyleProperties` تعریف شده است یا خیر.
اگر وجود داشته باشد، کنترلکنندههای رویداد دکمه را ایجاد میکنیم تا استایلهای درونخطی یا محاسبهای عنصر را دریافت کرده و نام و مقادیر آنها را ثبت کنیم.

```js
if (typeof window.CSSStyleProperties === "undefined") {
  log("CSSStyleProperties is not supported on this browser.");
} else {
  const element = document.querySelector("#elt");

  const inlineStyle = document.querySelector("#inline_style");
  inlineStyle.addEventListener("click", () => {
    clearLog();
    const elementStyle = element.style;
    getPopulatedProperties(elementStyle);
  });

  const computedStyle = document.querySelector("#computed_style");
  computedStyle.addEventListener("click", () => {
    clearLog();
    const compStyles = window.getComputedStyle(element);
    getPopulatedProperties(compStyles);
  });
}
```

#### نتایج

دکمهها را فشار دهید تا نام و مقادیر ویژگیهای خط تیرهدار استایل درونخطی و محاسبهای عنصر نمایش داده شود.
توجه کنید که استایلهای درونخطی فقط شامل استایلهایی هستند که روی خود عنصر تعریف شدهاند: همهٔ ویژگیهای دیگر مقدار `""` دارند و نمایش داده نمیشوند.
استایلهای محاسبهای همچنین شامل `font-weight` (که روی والد تعریف شده) و بسیاری از استایلهای محاسبهای دیگر هستند.

{{EmbedLiveSample("Enumerate dash-named style properties", "100", "400")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
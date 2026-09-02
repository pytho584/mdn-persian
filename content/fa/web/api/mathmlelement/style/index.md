---
title: "MathMLElement: style property"
short-title: style
slug: Web/API/MathMLElement/style
page-type: web-api-instance-property
browser-compat: api.MathMLElement.style
---

{{APIRef("CSSOM")}}

ویژگی **`style`** (فقط‌خواندنی) در رابط {{domxref("MathMLElement")}}، استایلِ _درون‌خطی_ [`style`](/en-US/docs/Web/HTML/Reference/Global_attributes/style) یک عنصر را به شکل یک شیء زنده از نوع {{domxref("CSSStyleProperties")}} برمی‌گرداند. با استفاده از این شیء می‌توان استایل‌های درون‌خطی یک عنصر را خواند و تنظیم کرد.

## مقدار

یک شیء زنده از نوع {{domxref("CSSStyleProperties")}}.

> [!NOTE]
> نسخه‌های پیشین مشخصات، یک {{domxref("CSSStyleDeclaration")}} را برمی‌گرداندند که {{domxref("CSSStyleProperties")}} از آن مشتق می‌شود. برای آگاهی از پشتیبانی مرورگرها به جدول [سازگاری مرورگر](#browser_compatibility) مراجعه کنید.

اگرچه خود ویژگی `style` از این نظر فقط‌خواندنی است که نمی‌توان شیء {{domxref("CSSStyleProperties")}} را با شیء دیگری جایگزین کرد، اما همچنان می‌توانید مستقیماً به ویژگی `style` مقدار بدهید؛ این کار معادل مقدار دادن به ویژگی {{domxref("CSSStyleDeclaration/cssText", "cssText")}} آن است. همچنین می‌توانید شیء {{domxref("CSSStyleProperties")}} را با روش‌های {{domxref("CSSStyleDeclaration/setProperty", "setProperty()")}} و {{domxref("CSSStyleDeclaration/removeProperty", "removeProperty()")}} تغییر دهید.

## توضیحات

مقادیر استایل‌های درون‌خطی که در ویژگی [`style`](/en-US/docs/Web/HTML/Reference/Global_attributes/style) عنصر تعیین شده‌اند، در ویژگی‌های متناظرِ شیءِ بازگشت‌داده‌شده {{domxref("CSSStyleProperties")}} منعکس می‌شوند.

> [!NOTE]
> {{domxref("CSSStyleProperties")}} برای **همه** [ویژگی‌های CSS](/en-US/docs/Web/CSS/Reference/Properties) پشتیبان‌شده توسط مرورگر، ویژگی‌های با نام خط تیره و همچنین ویژگی‌های متناظر با نام {{Glossary("camel_case", "camel-case")}} دارد؛ نه فقط آن‌هایی که استایل درون‌خطی دارند. ویژگی‌هایی که استایل درون‌خطی متناظر ندارند، روی `""` تنظیم شده‌اند.

ویژگی‌های CSS کوتاه‌نویس (shorthand) عنصر به ویژگی‌های بلندنویس (longhand) متناظرِ خود بسط داده می‌شوند. برای نمونه، عنصری با استایل `"border-top: 1px solid black"` در شیء بازگشت‌داده‌شده با ویژگی‌های دارای نام {{cssxref("border-top")}} و `borderTop`، و نیز ویژگی‌های بلندنویسِ متناظر یعنی {{cssxref("border-top-color")}} و `borderTopColor`، {{cssxref("border-top-style")}} و `borderTopStyle`، و {{cssxref("border-top-width")}} و `borderTopWidth` نمایش داده می‌شود.

ویژگی `style` فقط‌خواندنی است؛ یعنی نمی‌توان یک شیء {{domxref("CSSStyleProperties")}} را به آن اختصاص داد. با این حال، می‌توان با تخصیص مستقیم یک _رشته_ به این ویژگی، استایل درون‌خطی تنظیم کرد. در این حالت، رشته را می‌توان از روی {{domxref("CSSStyleDeclaration.cssText","cssText")}} خواند. به‌کارگیری `style` به این روش، همه استایل‌های درون‌خطی عنصر را کاملاً بازنویسی می‌کند.

برای افزودن استایل‌های مشخص به یک عنصر بدون دست زدن به سایر مقادیر استایل، معمولاً بهتر است ویژگی‌های جداگانه را روی شیء {{domxref("CSSStyleProperties")}} تنظیم کنید؛ مثلاً می‌توانید بنویسید `element.style.backgroundColor = "red"`. بازنشانی یک اعلان استایل با قرار دادن آن روی `null` یا یک رشته خالی انجام می‌شود؛ مانند `element.style.color = null`.

ویژگی `style` در آبشار CSS همان اولویت یک اعلان استایل درون‌خطی را دارد که از طریق ویژگی `style` تعیین شده باشد.

## مثال‌ها

### برشمردن اطلاعات استایل

#### HTML

```html
<math>
  <mrow>
    <mi>f</mi>
    <mo stretchy="false">(</mo>
    <mi class="parameter" style="color: red; border-bottom: 1px solid">x</mi>
    <mo stretchy="false">)</mo>
    <mo>=</mo>
    <mi>x</mi>
  </mrow>
</math>
<pre id="log"></pre>
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
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

```js
const element = document.querySelector(".parameter");
const elementStyle = element.style;

// Loop through all the element's styles using `for...in`
for (const prop in elementStyle) {
  // Check the property belongs to the CSSStyleProperties instance
  // Ensure the property is a numeric index (indicating a dash-named/inline style)
  if (
    Object.hasOwn(elementStyle, prop) &&
    !Number.isNaN(Number.parseInt(prop, 10))
  ) {
    log(
      `${
        elementStyle[prop]
      } = '${elementStyle.getPropertyValue(elementStyle[prop])}'`,
    );
  }
}
```

#### نتیجه

نتیجه در پایین نمایش داده شده است. توجه کنید که فقط ویژگی‌های بلندنویس CSS عنصر به‌صورت مقادیر برشمرده می‌شوند (ویژگی کوتاه‌نویس درون‌خطی برشمرده نمی‌شود).

{{EmbedLiveSample("Enumerating style information", "100", "150")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از اطلاعات استایل‌دهی پویا](/en-US/docs/Web/API/CSS_Object_Model/Using_dynamic_styling_information)
- {{domxref("HTMLElement.style")}}
- {{domxref("SVGElement.style")}}
- {{domxref("MathMLElement.attributeStyleMap")}}
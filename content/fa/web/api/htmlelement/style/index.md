---
title: "HTMLElement: style property"
short-title: style
slug: Web/API/HTMLElement/style
page-type: web-api-instance-property
browser-compat: api.HTMLElement.style
---

{{APIRef("CSSOM")}}

ویژگی فقط-خواندنی **`style`** در رابط {{domxref("HTMLElement")}}، شیوه‌نامه‌ی _درون‌خطی_ (inline) [`style`](/en-US/docs/Web/HTML/Reference/Global_attributes/style) یک عنصر را به صورت یک شیء زنده از نوع {{domxref("CSSStyleProperties")}} بازمی‌گرداند. از این شیء می‌توان برای دریافت و تنظیم شیوه‌های درون‌خطی یک عنصر استفاده کرد.

## مقدار

یک شیء زنده از نوع {{domxref("CSSStyleProperties")}}.

> [!NOTE]
> نسخه‌های قدیمی‌تر مشخصات، یک {{domxref("CSSStyleDeclaration")}} (که {{domxref("CSSStyleProperties")}} از آن مشتق شده است) را بازمی‌گرداندند.
> برای اطلاعات پشتیبانی مرورگرها، جدول [سازگاری مرورگر](#سازگاری_مرورگر) را ببینید.

اگرچه خود ویژگی `style` فقط-خواندنی است (به این معنا که نمی‌توانید شیء `CSSStyleProperties` را جایگزین کنید)، اما همچنان می‌توانید مستقیماً به ویژگی `style` مقداردهی کنید که معادل مقداردهی به ویژگی {{domxref("CSSStyleDeclaration/cssText", "cssText")}} آن است. همچنین می‌توانید شیء `CSSStyleProperties` را با استفاده از روش‌های {{domxref("CSSStyleDeclaration/setProperty", "setProperty()")}} و {{domxref("CSSStyleDeclaration/removeProperty", "removeProperty()")}} تغییر دهید.

## توضیحات

مقادیر شیوه‌های درون‌خطی تنظیم‌شده در ویژگی [`style`](/en-US/docs/Web/HTML/Reference/Global_attributes/style) عنصر، توسط ویژگی‌های متناظر در شیء برگشتی {{domxref("CSSStyleProperties")}} بازتاب داده می‌شوند.

> [!NOTE]
> {{domxref("CSSStyleProperties")}} دارای ویژگی‌های نام‌گذاری‌شده با خط تیره و همچنین نام‌گذاری‌شده با الگوی {{Glossary("camel_case", "camelCase")}} برای **تمام** ویژگی‌های [CSS](/en-US/docs/Web/CSS/Reference/Properties) پشتیبانی‌شده توسط مرورگر است (نه فقط آنهایی که شیوه درون‌خطی دارند). ویژگی‌هایی که شیوه درون‌خطی متناظر ندارند، روی `""` تنظیم می‌شوند.

ویژگی‌های CSS کوتاه‌نویس (shorthand) یک عنصر به ویژگی‌های بلندنویس (longhand) متناظر خود گسترش می‌یابند. برای مثال، یک عنصر با شیوه `"border-top: 1px solid black"` در شیء برگشتی با ویژگی‌های دارای نام {{cssxref("border-top")}} و `borderTop`، و همچنین ویژگی‌های بلندنویس متناظر یعنی {{cssxref("border-top-color")}} و `borderTopColor`، {{cssxref("border-top-style")}} و `borderTopStyle`، و {{cssxref("border-top-width")}} و `borderTopWidth` نمایش داده می‌شود.

برای افزودن شیوه‌های خاص به یک عنصر بدون تغییر سایر مقادیر شیوه، معمولاً بهتر است ویژگی‌های جداگانه روی شیء {{domxref("CSSStyleProperties")}} تنظیم شوند. برای مثال می‌توانید بنویسید `element.style.backgroundColor = "red"`. یک اعلان شیوه با تنظیم آن به `null` یا یک رشته خالی بازنشانی می‌شود، مانند: `element.style.color = null`.

ویژگی `style` در آبشار CSS همان اولویتی را دارد که یک اعلان شیوه درون‌خطی تنظیم‌شده از طریق ویژگی `style` دارد.

## مثال‌ها

### استفاده پایه

این مثال کد نشان می‌دهد که چگونه می‌توان شیوه‌های درون‌خطی یک عنصر را خواند. در هر مورد، ویژگی‌های شیوه با نام خط تیره‌دار با استفاده از {{DOMxRef("CSSStyleDeclaration/getPropertyPriority", "getPropertyValue()")}} خوانده می‌شوند و ویژگی‌های camelCase با استفاده از عملگر نقطه (dot) دریافت می‌شوند.

#### HTML

ابتدا یک عنصر {{htmlelement("div")}} و یک عنصر تو در تو تعریف می‌کنیم که شیوه‌های درون‌خطی متفاوتی را با استفاده از هر دو حالت کوتاه‌نویس و بلندنویس تعریف می‌کنند.

```html
<div style="font-weight: bold;">
  <div style="border-top: 1px solid blue; color: red;" id="elt">
    یک div نمونه
  </div>
  <pre id="log"></pre>
</div>
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
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

کد زیر عنصر داخلی را دریافت می‌کند، شیوه آن را می‌خواند و ویژگی‌های شیوه CSS با نام خط تیره‌دار و camelCase را ثبت می‌کند.

```js
const element = document.getElementById("elt");
const elementStyle = element.style;

// شیوه‌های بلندنویس
log(`"border-top" = '${elementStyle.getPropertyValue("border-top")}'`);
log(`"borderTop" = '${elementStyle.borderTop}'`);

// شیوه‌های بلندنویس گسترش‌یافته
log(
  `"border-top-width" = '${elementStyle.getPropertyValue("border-top-width")}'`,
);
log(`"borderTopWidth" = '${elementStyle.borderTopWidth}'`);

log(
  `"border-top-style" = '${elementStyle.getPropertyValue("border-top-style")}'`,
);
log(`"borderTopStyle" = '${elementStyle.borderTopStyle}'`);

log(
  `"border-top-color" = '${elementStyle.getPropertyValue("border-top-color")}'`,
);
log(`"borderTopColor" = '${elementStyle.borderTopColor}'`);

// شیوه کوتاه‌نویس اصلی
log(`"color" = '${elementStyle.getPropertyValue("color")}'`);
log(`"color" = '${elementStyle.color}'`);

// تعریف‌شده روی والد
log(`"font-weight" = '${elementStyle.getPropertyValue("font-weight")}'`);
log(`"fontWeight" = '${elementStyle.fontWeight}'`);
```

#### نتایج

نتیجه در زیر نشان داده شده است. در هر مورد می‌بینیم که شیوه‌های خوانده‌شده با استفاده از ویژگی‌های نام خط تیره‌دار و camelCase یکسان هستند. همچنین می‌بینیم که ویژگی {{cssxref("border-top")}} متناظر با ویژگی `style` عنصر وجود دارد و یک ویژگی بلندنویس برای هر یک از اجزای آن ({{cssxref("border-top-color")}}، {{cssxref("border-top-style")}}، و {{cssxref("border-top-width")}}) تعریف شده است.

{{EmbedLiveSample("استفاده پایه", "100", "280")}}

توجه کنید که `font-weight` روی `CSSStyleProperties` تعریف شده است (همانند سایر ویژگی‌های CSS، اگرچه ما آنها را ثبت نکرده‌ایم). با این حال، این یک شیوه درون‌خطی برای عنصر تودرتو نیست، بنابراین مقدار آن روی رشته خالی (`""`) تنظیم شده است.

### شمارش اطلاعات شیوه

این مثال نشان می‌دهد که چگونه می‌توان ویژگی‌های با نام خط تیره‌دار {{domxref("CSSStyleProperties")}} را شمارش کرد.

#### HTML

ابتدا یک عنصر {{htmlelement("div")}} و یک عنصر تودرتو تعریف می‌کنیم که شیوه‌های درون‌خطی متفاوتی را با استفاده از هر دو حالت کوتاه‌نویس و بلندنویس تعریف می‌کنند. این همان HTML مثال قبلی است.

```html
<div style="font-weight: bold;">
  <div style="border-top: 1px solid blue; color: red;" id="elt">
    یک div نمونه
  </div>
  <pre id="log"></pre>
</div>
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

کد زیر ویژگی‌های قابل شمارش `CSSStyleProperties` را پیمایش می‌کند و نتیجه را ثبت می‌کند.

```js
const element = document.getElementById("elt");
const elementStyle = element.style;

// پیمایش همه شیوه‌های عنصر با استفاده از `for...in`
for (const prop in elementStyle) {
  // بررسی اینکه ویژگی متعلق به نمونه CSSStyleProperties است
  // اطمینان از اینکه ویژگی یک شاخص عددی است (نشان‌دهنده شیوه با نام خط تیره‌دار/درون‌خطی)
  if (
    Object.hasOwn(elementStyle, prop) &&
    !Number.isNaN(Number.parseInt(prop, 10))
  ) {
    log(
      `${
        elementStyle[prop]
      } = '${elementStyle.getPropertyValue(elementStyle[prop])}`,
    );
  }
}
```

#### نتایج

نتیجه در زیر نشان داده شده است. توجه کنید که فقط ویژگی‌های بلندنویس CSS عنصر به عنوان مقادیر شمارش‌شده ظاهر می‌شوند (ویژگی کوتاه‌نویس درون‌خطی شمارش نمی‌شود).

{{EmbedLiveSample("شمارش اطلاعات شیوه", "100", "180")}}

### به‌روزرسانی شیوه حاشیه

```html
<div id="box"></div>

<button id="btn1">حاشیه ۲۰ پیکسل</button>
<button id="btn2">حاشیه ۵ پیکسل</button>
```

```css
#box {
  border: 5px solid green;
  width: 100px;
  height: 100px;
}
```

```js
function setBorderWidth(width) {
  document.getElementById("box").style.borderWidth = `${width}px`;
}

document.getElementById("btn1").addEventListener("click", () => {
  setBorderWidth(20);
});
document.getElementById("btn2").addEventListener("click", () => {
  setBorderWidth(5);
});
```

{{EmbedLiveSample("به‌روزرسانی شیوه حاشیه", "", "200")}}

### دستکاری شیوه‌ها

در این مثال، برخی ویژگی‌های شیوه پایه یک عنصر پاراگراف HTML با استفاده از شیء style روی عنصر و ویژگی‌های شیوه CSS آن شیء که می‌توان از DOM دریافت و تنظیم کرد، دسترسی داده می‌شوند. در این حالت، شما مستقیماً شیوه‌های فردی را دستکاری می‌کنید. همچنین می‌توانید از {{domxref("document.styleSheets", "styleSheets")}} و قوانین آنها برای تغییر شیوه‌های کل اسناد استفاده کنید.

```html
<p id="pid">متن</p>
<p><button type="button">تغییر متن</button></p>
```

```js
function changeText() {
  const p = document.getElementById("pid");

  p.style.color = "blue";
  p.style.fontSize = "18pt";
}

document.querySelector("button").addEventListener("click", () => {
  changeText();
});
```

{{EmbedLiveSample("دستکاری شیوه‌ها", "", "200")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [استفاده از اطلاعات شیوه‌دهی پویا](/en-US/docs/Web/API/CSS_Object_Model/Using_dynamic_styling_information)
- {{domxref("SVGElement.style")}}
- {{domxref("MathMLElement.style")}}
- {{domxref("HTMLElement.attributeStyleMap")}}
- ویژگی HTML [`style`](/en-US/docs/Web/HTML/Reference/Global_attributes/style)
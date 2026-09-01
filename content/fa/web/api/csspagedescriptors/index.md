---
title: CSSPageDescriptors
slug: Web/API/CSSPageDescriptors
page-type: web-api-interface
browser-compat: api.CSSPageDescriptors
---

{{APIRef("CSSOM")}}

**`CSSPageDescriptors`** واسطهای است که یک بلوک اعلان CSS را برای یک [at-rule](/en-US/docs/Web/CSS/Guides/Syntax/At-rules) از نوع {{cssxref("@page")}} نشان میدهد.

این واسطه اطلاعات سبک و همچنین روشها و ویژگیهای مختلف مرتبط با سبک را برای صفحه در معرض قرار میدهد. هر ویژگی چندکلمهای نسخههایی به شکل camel-case و snake-case دارد. برای مثال، این بدان معناست که میتوانید به ویژگی CSS `margin-top` با استفاده از نحو `style["margin-top"]` یا `style.marginTop` دسترسی داشته باشید (در حالی که `style` یک `CSSPageDescriptor` است).

یک شیء `CSSPageDescriptors` از طریق ویژگی {{DOMxRef("CSSPageRule.style", "style")}} از واسط `CSSPageRule` در دسترس است، که به نوبه خود میتواند با استفاده از API {{DOMxRef("CSSStyleSheet")}} یافت شود.

{{InheritanceDiagram}}

## ویژگیهای نمونه

_این واسطه همچنین ویژگیهای والد خود، {{domxref("CSSStyleDeclaration")}} را به ارث میبرد._

نام ویژگیهای زیر، به صورت kebab-case (دسترسی با [نحو براکت](/en-US/docs/Learn_web_development/Core/Scripting/Object_basics#bracket_notation)) و camel-case (دسترسی با [نحو نقطه](/en-US/docs/Learn_web_development/Core/Scripting/Object_basics#dot_notation))، هر کدام مقدار یک توصیفگر (descriptor) را در at-rule متناظر `@page` نشان میدهند:

- `margin`
  - : یک رشته که ویژگی `margin` مربوطه در at-rule `@page` را نشان میدهد.
- `margin-top` یا `marginTop`
  - : یک رشته که ویژگی `margin-top` مربوطه در at-rule `@page` را نشان میدهد.
- `margin-right` یا `marginRight`
  - : یک رشته که ویژگی `margin-right` مربوطه در at-rule `@page` را نشان میدهد.
- `margin-bottom` یا `marginBottom`
  - : یک رشته که ویژگی `margin-bottom` مربوطه در at-rule `@page` را نشان میدهد.
- `margin-left` یا `marginLeft`
  - : یک رشته که ویژگی `margin-left` مربوطه در at-rule `@page` را نشان میدهد.
- `page-orientation` یا `pageOrientation` {{experimental_inline}}
  - : یک رشته که ویژگی `page-orientation` مربوطه در at-rule `@page` را نشان میدهد.
- `size`
  - : یک رشته که ویژگی `size` مربوطه در at-rule `@page` را نشان میدهد.

## روشهای نمونه

_این واسطه روشهای والد خود، {{domxref("CSSStyleDeclaration")}} را به ارث میبرد._

## مثالها

### بررسی یک at-rule صفحه

این مثال `CSSPageDescriptors` را برای یک at-rule از نوع {{cssxref("@page")}} دریافت میکند (در صورتی که شیء در مرورگر پشتیبانی شود) و سپس ویژگیهای آن را در خروجی ثبت میکند.

```html hidden
<pre id="log"></pre>
```

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

```css hidden
#log {
  height: 280px;
  overflow: scroll;
  padding: 0.5rem;
  border: 1px solid black;
}
```

#### CSS

در زیر، با استفاده از یک at-rule از نوع {{cssxref("@page")}}، سبکها را برای صفحه تعریف میکنیم. برای هر ویژگی margin مقدار متفاوتی با استفاده از شکل کوتاه‌شده `margin` اختصاص میدهیم و همچنین `size` را مشخص میکنیم. مقدار `page-orientation` را تنظیم نمیکنیم. این کار به ما امکان میدهد ببینیم ویژگیها چگونه در شیء Web API نگاشت میشوند.

```css
@page {
  margin: 1cm 2px 3px 4px;
  /* page-orientation: upright; */
  size: A4;
}
```

#### JavaScript

ابتدا بررسی میکنیم که آیا `CSSPageDescriptors` در شیء سراسری window تعریف شده است یا نه؛ اگر تعریف نشده بود، این پیام را ثبت میکنیم که واسطه پشتیبانی نمیشود.

اگر `CSSPageDescriptors` پشتیبانی میشود، شیوه‌نامه هدف را دریافت کرده و سپس `cssRules` تعریف‌شده در آن را میگیریم. باید این شیوه‌نامه را به دست آوریم، زیرا مثال در یک فریم جداگانه با شیوه‌نامه خاص خود جاسازی شده است (اندیس `0` مربوط به CSS این صفحه است).

سپس روی قواعد تعریف‌شده برای مثال زنده پیمایش میکنیم و هر قاعده‌ای را که از نوع `CSSPageRule` است، مطابقت میدهیم، زیرا این قواعد معادل قواعد `@page` هستند. برای اشیاء مطابقت‌یافته، `style` و تمام مقادیر آن را در خروجی ثبت میکنیم.

```js
if (typeof window.CSSPageDescriptors === "undefined") {
  log("CSSPageDescriptors is not supported on this browser.");
} else {
  // Get stylesheets for example and then get its cssRules
  const myRules = document.getElementById("css-output").sheet.cssRules;
  for (const rule of myRules) {
    if (rule instanceof CSSPageRule) {
      log(`${rule.style}`);
      log(`margin: ${rule.style.margin}`);

      // Access properties using CamelCase syntax
      log(`marginTop: ${rule.style.marginTop}`);
      log(`marginRight: ${rule.style.marginRight}`);
      log(`marginBottom: ${rule.style.marginBottom}`);
      log(`marginLeft: ${rule.style.marginLeft}`);
      log(`pageOrientation: ${rule.style.pageOrientation}`);

      // Access properties using snake-case syntax
      log(`margin-top: ${rule.style["margin-top"]}`);
      log(`margin-right: ${rule.style["margin-right"]}`);
      log(`margin-left: ${rule.style["margin-left"]}`);
      log(`margin-bottom: ${rule.style["margin-bottom"]}`);
      log(`page-orientation: ${rule.style["page-orientation"]}`);

      log(`size: ${rule.style.size}`);

      // Log the original CSS text using inherited property: cssText
      log(`cssText: ${rule.style.cssText}`);
      log("\n");
    }
  }
}
```

#### نتایج

نتایج در زیر نشان داده شده است. توجه داشته باشید که شیء `style` نمایش‌داده‌شده در بالای خروجی، برای مطابقت با مشخصات فعلی باید یک `CSSPageDescriptors` باشد، اما در برخی مرورگرها ممکن است یک `CSSStyleDeclaration` باشد. همچنین توجه کنید که مقادیر متناظر برای ویژگیها در شکل camel-case و snake-case با یکدیگر و با اعلان `@page` مطابقت دارند و `page-orientation` رشته خالی `""` است، زیرا در `@page` تعریف نشده است.

{{EmbedLiveSample("Inspecting a page at-rule", "100%", "350px")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
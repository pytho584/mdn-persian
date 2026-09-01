---
title: "CSSPageRule: style property"
short-title: style
slug: Web/API/CSSPageRule/style
page-type: web-api-instance-property
browser-compat: api.CSSPageRule.style
---

{{APIRef("CSSOM")}}

ویژگی فقط‌خواندنی **`style`** در رابط {{domxref("CSSPageRule")}} شامل یک شیء {{domxref("CSSPageDescriptors")}} است که توصیف‌گرهای (descriptors) موجود در بدنهٔ قانون {{cssxref("@page")}} را نمایش می‌دهد.

## مقدار

یک شیء {{domxref("CSSPageDescriptors")}}.

> [!NOTE]
> نسخه‌های قبلی مشخصات، این ویژگی را به‌عنوان یک {{domxref("CSSStyleDeclaration")}} تعریف کرده بودند.
> برای مرورگر خود، داده‌های سازگاری زیر را بررسی کنید.

اگرچه خود ویژگی `style` از این نظر فقط‌خواندنی است که نمی‌توانید شیء `CSSPageDescriptors` را جایگزین کنید، اما همچنان می‌توانید مستقیماً به `style` مقدار نسبت دهید که معادل نسبت دادن به ویژگی {{domxref("CSSStyleDeclaration/cssText", "cssText")}} آن است. همچنین می‌توانید شیء `CSSPageDescriptors` را با استفاده از روش‌های {{domxref("CSSStyleDeclaration/setProperty", "setProperty()")}} و {{domxref("CSSStyleDeclaration/removeProperty", "removeProperty()")}} تغییر دهید.

## مثال‌ها

### بررسی یک قانون صفحه

این مثال از Web API برای بررسی محتوای یک قانون {{cssxref("@page")}} استفاده می‌کند.

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
  height: 230px;
  overflow: scroll;
  padding: 0.5rem;
  border: 1px solid black;
}
```

#### CSS

در زیر، سبک‌های صفحه را با استفاده از یک قانون {{cssxref("@page")}} تعریف می‌کنیم.
برای هر ویژگی حاشیه (margin) با استفاده از شكل کوتاه‌شدهٔ `margin` مقادیر مختلفی تعیین می‌کنیم و همچنین `size` را مشخص می‌کنیم.
ویژگی `page-orientation` را تنظیم نمی‌کنیم.
این به ما امکان می‌دهد ببینیم ویژگی‌ها چگونه در شیء Web API نگاشت می‌شوند.

```css
@page {
  margin: 1cm 2px 3px 4px;
  /* page-orientation: upright; */
  size: A4;
}
```

#### جاوااسکریپت

زیرساخت [نمونه زنده](/en-US/docs/MDN/Writing_guidelines/Page_structures/Live_samples) MDN تمام بلوک‌های CSS موجود در مثال را در یک استایل درون‌خطی با شناسه `css-output` ترکیب می‌کند، بنابراین ابتدا از {{domxref("document.getElementById()")}} برای یافتن آن شیوه‌نامه استفاده می‌کنیم.

```js
const myRules = document.getElementById("css-output").sheet.cssRules;
```

سپس روی قوانین تعریف‌شده برای مثال زنده پیمایش می‌کنیم و هر قاعده‌ای را که از نوع `CSSPageRule` باشد مطابقت می‌دهیم، زیرا این قوانین معادل قانون‌های `@page` هستند.
برای اشیاء مطابق‌شده، سپس `style` و تمام مقادیر آن را ثبت می‌کنیم.

```js
for (const rule of myRules) {
  if (rule instanceof CSSPageRule) {
    log(`${rule.style}`);
    log(`margin: ${rule.style.margin}`);

    // دسترسی به ویژگی‌ها با استفاده از نام‌های camelCase
    log(`marginTop: ${rule.style.marginTop}`);
    log(`marginRight: ${rule.style.marginRight}`);
    log(`marginBottom: ${rule.style.marginBottom}`);
    log(`marginLeft: ${rule.style.marginLeft}`);
    log(`pageOrientation: ${rule.style.pageOrientation}`);

    // دسترسی به ویژگی‌ها با استفاده از نام‌های خط تیره‌دار
    log(`margin-top: ${rule.style["margin-top"]}`);
    log(`margin-right: ${rule.style["margin-right"]}`);
    log(`margin-left: ${rule.style["margin-left"]}`);
    log(`margin-bottom: ${rule.style["margin-bottom"]}`);
    log(`page-orientation: ${rule.style["page-orientation"]}`);

    log(`size: ${rule.style.size}`);
    log("\n");
  }
}
```

#### نتایج

نتایج در زیر نشان داده شده است.
توجه داشته باشید که شیء باید یک `CSSPageDescriptors` باشد تا با مشخصات فعلی مطابقت داشته باشد، اما ممکن است در برخی مرورگرها یک `CSSStyleDeclaration` باشد.
همچنین توجه داشته باشید که مقادیر متناظر برای ویژگی‌ها در حالت camelCase و خط تیره‌دار با یکدیگر و با اعلان `@page` مطابقت دارند و `page-orientation` رشتهٔ خالی `""` است چون در `@page` تعریف نشده است.

{{EmbedLiveSample("Inspecting a page rule", "100%", "300px")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
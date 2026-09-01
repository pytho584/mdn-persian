---
title: CSSMediaRule
slug: Web/API/CSSMediaRule
page-type: web-api-interface
browser-compat: api.CSSMediaRule
---

{{ APIRef("CSSOM") }}

رابط **`CSSMediaRule`** نمایانگر یک قانون تکی {{cssxref("@media")}} در CSS است.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌ها را از اجداد خود یعنی {{domxref("CSSConditionRule")}}، {{domxref("CSSGroupingRule")}} و {{domxref("CSSRule")}} به ارث می‌برد._

- {{domxref("CSSMediaRule.media")}} {{ReadOnlyInline}}
  - : یک {{domxref("MediaList")}} برمی‌گرداند که نمایانگر رسانهٔ مقصدِ موردنظر برای اطلاعات استایل است.

## متدهای نمونه

_متد خاصی ندارد؛ متدها را از اجداد خود یعنی {{domxref("CSSConditionRule")}}، {{domxref("CSSGroupingRule")}} و {{domxref("CSSRule")}} به ارث می‌برد._

## مثال‌ها

CSS زیر شامل یک media query با یک قانون استایل است. زیرساخت [نمونهٔ زندهٔ MDN](/en-US/docs/MDN/Writing_guidelines/Page_structures/Live_samples) تمام بلوک‌های CSS موجود در مثال را در یک استایل درون‌خطی با شناسهٔ `css-output` ترکیب می‌کند؛ بنابراین ابتدا با استفاده از {{domxref("document.getElementById()")}} آن شیوه‌نامه را پیدا می‌کنیم. `myRules[0]` یک شیء `CSSMediaRule` برمی‌گرداند که می‌توانیم `mediaText` را از آن دریافت کنیم.

```html
<p id="log"></p>
```

```css
@media (width >= 500px) {
  body {
    color: blue;
  }
}
```

```js
const log = document.getElementById("log");
const myRules = document.getElementById("css-output").sheet.cssRules;
const mediaList = myRules[0]; // a CSSMediaRule representing the media query.
log.textContent += ` ${mediaList.media.mediaText}`;
```

{{EmbedLiveSample("Examples","100%","50px")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
```
---
title: "MathMLElement: attributeStyleMap property"
short-title: attributeStyleMap
slug: Web/API/MathMLElement/attributeStyleMap
page-type: web-api-instance-property
browser-compat: api.MathMLElement.attributeStyleMap
---

{{APIRef("CSSOM")}}

ویژگی فقط‌خواندنی **`attributeStyleMap`** در رابط {{domxref("MathMLElement")}} یک شیء زنده از {{domxref("StylePropertyMap")}} برمی‌گرداند که شامل فهرستی از ویژگی‌های سبک عنصر است؛ آن دسته از ویژگی‌هایی که در ویژگیِ درون‌خطیِ `style` عنصر تعریف شده‌اند یا از طریق اسکریپت و با استفاده از ویژگی {{domxref("MathMLElement.style", "style")}} در رابط {{domxref("MathMLElement")}} اختصاص داده شده‌اند.

ویژگی‌های کوتاه‌نویسی (Shorthand) به شکل بلند (Longhand) بسط داده می‌شوند. برای مثال، اگر `border-top: 1px solid black` را تنظیم کنید، به جای آن ویژگی‌های بلند ({{cssxref("border-top-color")}}، {{cssxref("border-top-style")}} و {{cssxref("border-top-width")}}) تنظیم می‌شوند.

تفاوت اصلی بین ویژگی {{domxref("MathMLElement.style", "style")}} و ویژگی `attributeStyleMap` در این است که ویژگی `style` یک شیء {{domxref("CSSStyleDeclaration")}} برمی‌گرداند، در حالی که ویژگی `attributeStyleMap` یک شیء {{domxref("StylePropertyMap")}} برمی‌گرداند.

هرچند خودِ این ویژگی قابل نوشتن نیست، اما می‌توانید از طریق شیء {{domxref("StylePropertyMap")}} که برمی‌گرداند، سبک‌های درون‌خطی را بخوانید و بنویسید، دقیقاً مانند شیء {{domxref("CSSStyleDeclaration")}} که از طریق ویژگی `style` به دست می‌آید.

## مقدار

یک شیء زنده از {{domxref("StylePropertyMap")}}.

## مثال‌ها

قطعه کد زیر رابطه بین ویژگی `style` و ویژگی `attributeStyleMap` را نشان می‌دهد:

```html
<math>
  <mrow>
    <mi>f</mi>
    <mo stretchy="false">(</mo>
    <mi id="el" style="border-top: 1px solid blue; color: red;">x</mi>
    <mo stretchy="false">)</mo>
    <mo>=</mo>
    <mi>x</mi>
  </mrow>
</math>
<div id="output"></div>
```

```css
#el {
  font-size: 16px;
}

#output {
  white-space: pre-line;
}
```

```js
const element = document.getElementById("el");
const output = document.getElementById("output");

for (const property of element.attributeStyleMap) {
  output.textContent += `${property[0]} = ${property[1][0].toString()}\n`;
}
```

{{EmbedLiveSample("Examples", "200", "200")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("MathMLElement.style")}}
- {{domxref("HTMLElement.attributeStyleMap")}}
- {{domxref("SVGElement.attributeStyleMap")}}
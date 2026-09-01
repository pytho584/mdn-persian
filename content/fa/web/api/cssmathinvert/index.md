---
title: "CSSMathInvert"
---

---
title: CSSMathInvert
slug: Web/API/CSSMathInvert
page-type: web-api-interface
browser-compat: api.CSSMathInvert
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

رابطِ **`CSSMathInvert`** در [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Object_Model) وارون (معکوس) یک {{domxref('CSSNumericValue')}} را نمایش می‌دهد.

{{InheritanceDiagram}}

## سازنده

- {{domxref("CSSMathInvert.CSSMathInvert", "CSSMathInvert()")}}
  - : یک شیء `CSSMathInvert` جدید می‌سازد.

## ویژگی‌های نمونه

_همچنین ویژگی‌های رابط والد خود، {{DOMxRef("CSSMathValue")}} را به ارث می‌برد._

- {{domxref('CSSMathInvert.value')}} {{ReadOnlyInline}}
  - : یک شیء {{domxref('CSSNumericValue')}} حاوی مقداری که قرار است معکوس شود را بازمی‌گرداند.

## روش‌های ایستا

_همچنین روش‌های رابط والد خود، {{DOMxRef("CSSMathValue")}} را به ارث می‌برد._

## روش‌های نمونه

_همچنین روش‌های رابط والد خود، {{DOMxRef("CSSMathValue")}} را به ارث می‌برد._

## توضیحات

وقتی یک {{domxref('CSSNumericValue')}} را با استفاده از {{domxref('CSSNumericValue.div', 'div()')}} بر مقدار دیگری تقسیم می‌کنید، اگر مقسوم‌علیه یک عدد ساده باشد، بلافاصله می‌تواند به مقداری از همان نوع اصلی مقیاس‌بندی شود.

اگر مقسوم‌علیه از نوع دیگری باشد، نتیجه را نمی‌توان به یک شیء واحد تبدیل کرد. در این حالت، [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Object_Model) مقسوم‌علیه را به صورت یک `CSSMathInvert` نمایش می‌دهد.

به‌طور معمول شما مستقیماً یک `CSSMathInvert` نمی‌سازید. این شیء زمانی تولید می‌شود که `div()` با مقسوم‌علیه‌ای غیر از عدد ساده فراخوانی شود: نتیجه یک {{domxref('CSSMathProduct')}} است و `CSSMathInvert` عملوندی است که آن مقسوم‌علیه را نگه می‌دارد — که با پیمایش عملوندهای حاصل‌ضرب، یا با بررسی {{domxref('CSSMathValue.operator')}} برای رشته `"invert"` پیدا می‌شود.

`CSSMathInvert` با استفاده از نحو CSS {{CSSXref('calc','calc()')}} به صورت `calc(1 / <value>)` سریال‌سازی می‌شود.

## مثال‌ها

### ساخت CSSMathInvert با مقسوم‌علیه غیرعددی

این مثال نشان می‌دهد که چگونه می‌توانید از {{domxref('CSSNumericValue.div', 'div()')}} با مقسوم‌علیه‌ای که عدد ساده نیست استفاده کنید تا یک {{domxref('CSSMathProduct')}} به دست آورید که یکی از عملوندهای آن `CSSMathInvert` است. مقدار و سریال‌سازی آن عملوند نیز در خروجی ثبت می‌شود.

```js
const product = CSS.px(200).div(CSS.percent(4));

console.log(product.constructor.name); // "CSSMathProduct"
console.log(product.values[1].constructor.name); // "CSSMathInvert"
console.log(product.values[1].value); // CSSUnitValue {value: 4, unit: "percent"}
console.log(product.toString()); // "calc(200px / 4%)"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CSSNumericValue.div", "div()")}}
- {{domxref("CSSMathNegate")}}
- {{domxref("CSSMathValue.operator")}}
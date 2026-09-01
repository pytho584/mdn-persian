---
title: CSSMathNegate
slug: Web/API/CSSMathNegate
page-type: web-api-interface
browser-compat: api.CSSMathNegate
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

**`CSSMathNegate`** یک رابط (interface) در [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Object_Model) است که قرینه (نفی) یک {{domxref("CSSNumericValue")}} را نشان میدهد.

{{InheritanceDiagram}}

## سازنده

- {{domxref("CSSMathNegate.CSSMathNegate", "CSSMathNegate()")}}
  - : یک شیء `CSSMathNegate` جدید می‌سازد.

## ویژگی‌های نمونه

_همچنین ویژگی‌های رابط والد خود، {{DOMxRef("CSSMathValue")}} را به ارث می‌برد._

- {{domxref("CSSMathNegate.value")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref("CSSNumericValue")}} برمی‌گرداند.

## متدهای استاتیک

_همچنین متدهای رابط والد خود، {{DOMxRef("CSSMathValue")}} را به ارث می‌برد._

## متدهای نمونه

_همچنین متدهای رابط والد خود، {{DOMxRef("CSSMathValue")}} را به ارث می‌برد._

## توضیحات

`CSSMathNegate` معادل اعمال عملگر «منفی یکانی» (unary minus) روی یک مقدار عددی است (`x` به `-x` تبدیل می‌شود).

به‌طور معمول مستقیماً یک `CSSMathNegate` نمی‌سازید. این شیء در مرحله قرینه‌سازی داخلی ایجاد می‌شود که {{domxref("CSSNumericValue.sub", "sub()")}} قبل از جمع کردن آرگومان‌ها روی آن‌ها اعمال می‌کند: قرینه کردن یک {{domxref("CSSMathSum")}}، {{domxref("CSSMathProduct")}}، {{domxref("CSSMathMin")}}، {{domxref("CSSMathMax")}}، {{domxref("CSSMathClamp")}} یا {{domxref("CSSMathInvert")}} آن را در یک `CSSMathNegate` می‌پیچد. اما قرینه کردن یک {{domxref("CSSUnitValue")}} ساده (یک طول، درصد و غیره) به‌جای آن، علامت `value` آن را مستقیماً برعکس می‌کند؛ بنابراین تفریق مقادیر ساده معمولاً یک `CSSMathNegate` تولید نمی‌کند.

همچنین ممکن است هنگام خواندن یک مقدار محاسبه‌شده (computed value) با `CSSMathNegate` مواجه شوید: برای مثال، فراخوانی {{domxref("StylePropertyMapReadOnly.get", "get()")}} روی ویژگی‌ای که با یک عبارت {{cssxref("calc", "calc()")}} حاوی تفریق مقدار تنظیم شده باشد، یک {{domxref("CSSMathSum")}} برمی‌گرداند که عملوندهای آن ممکن است شامل یک `CSSMathNegate` باشند. این نوع شیء را می‌توانید با بررسی خاصیت {{domxref("CSSMathValue.operator", "operator")}} و مقایسه آن با رشته `"negate"` شناسایی کنید.

`CSSMathNegate` با استفاده از نحو CSS {{CSSXref("calc", "calc()")}} به صورت `calc(-<value>)` سریال‌سازی می‌شود.

## مثال‌ها

### کاربرد پایه

کد زیر یک شیء `CSSMathNegate` از یک طول می‌سازد و سپس نام سازنده، `value` و سریال‌سازی شیء (از طریق {{domxref("CSSStyleValue/toString","toString()")}}) را در کنسول ثبت می‌کند.

```js
const negated = new CSSMathNegate(CSS.px(10));

console.log(negated.constructor.name); // "CSSMathNegate"
console.log(negated.value); // CSSUnitValue {value: 10, unit: "px"}
console.log(negated.toString()); // "calc(-10px)"
```

توجه داشته باشید که اگر یک عدد ساده به `arg` داده شود، `value` به یک {{domxref("CSSUnitValue")}} با واحد `"number"` تبدیل می‌شود:

```js
const negatedNumber = new CSSMathNegate(4);

console.log(negatedNumber.value); // CSSUnitValue {value: 4, unit: "number"}
console.log(negatedNumber.toString()); // "calc(-4)"
```

### تفریق یک مقدار ترکیبی

{{domxref("CSSNumericValue.sub", "sub()")}} زمانی `CSSMathNegate` تولید می‌کند که مقدار مورد تفریق، خود یک مقدار ترکیبی (composite value) باشد، مانند `CSSMathSum` (و نه یک {{domxref("CSSUnitValue")}} ساده).

این موضوع در کد زیر نشان داده شده است. `px` و `percent` بدون دانستن اندازه بلوک شامل (containing block) نمی‌توانند در یک مقدار واحد ترکیب شوند، بنابراین مقدار `composite` به صورت یک `CSSMathSum` نمایش داده می‌شود. وقتی این مقدار تفریق شود، مقدار `composite` در یک `CSSMathNegate` قرار می‌گیرد.

```js
const composite = CSS.px(10).add(CSS.percent(5)); // CSSMathSum: calc(10px + 5%)
const result = CSS.px(100).sub(composite);

console.log(result.constructor.name); // "CSSMathSum"
console.log(result.values[1].constructor.name); // "CSSMathNegate"
console.log(result.values[1].value); // CSSMathSum {values: CSSNumericArray, operator: "sum"}
console.log(result.toString()); // "calc(100px - (10px + 5%))"
```

### تجزیه‌ی `calc()`

یک `CSSMathNegate` همچنین می‌تواند هنگام استفاده از {{domxref("CSSStyleValue/parse_static", "CSSStyleValue.parse()")}} برای تجزیه یک عبارت {{cssxref("calc", "calc()")}} که نمی‌توان به یک مقدار واحد تقلیل داد، ایجاد شود.

برای مثال، در کد زیر {{domxref("CSSStyleValue/parse_static", "CSSStyleValue.parse()")}} مقدار ویژگی `width` را تجزیه می‌کند که یک طول را از یک درصد کم می‌کند (این دو تا زمان layout نمی‌توانند ترکیب شوند). نتیجه یک {{domxref("CSSMathSum")}} است که اولین مقدار در آرایه یک `CSSUnitValue` و دومین مقدار یک شیء `CSSMathNegate` است که قرینه عملوند دوم ارسال‌شده به تابع `calc()` را نمایش می‌دهد.

```js
const width = CSSStyleValue.parse("width", "calc(50% - 10px)");

console.log(width.constructor.name); // "CSSMathSum"
console.log(width.values[0]); // CSSUnitValue {value: 50, unit: 'percent'}
console.log(width.values[1]); // CSSMathNegate {value: CSSUnitValue, operator: 'negate'}
console.log(width.values[1].value); // CSSUnitValue {value: 10, unit: "px"}

console.log(width.toString()); // "calc(50% - 10px)"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CSSNumericValue.sub", "sub()")}}
- {{domxref("CSSStyleValue/parse_static", "CSSStyleValue.parse()")}}
- {{domxref("CSSMathInvert")}}
- {{domxref("CSSMathValue.operator")}}
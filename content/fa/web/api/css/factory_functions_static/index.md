---
title: "توابع عددی CSS"
slug: Web/API/CSS/factory_functions_static
page-type: web-api-static-method
browser-compat: api.CSS
spec-urls: https://drafts.css-houdini.org/css-typed-om/#numeric-factory
---

{{APIRef("CSSOM")}}

**توابع عددی CSS**، مانند `CSS.em()` و `CSS.turn()`، متدهایی هستند که یک {{domxref("CSSUnitValue")}} برمی‌گردانند؛ مقدار آن برابر با آرگومان عددی و واحد آن برابر با نام متد استفاده‌شده است. این توابع مقادیر عددی جدید را با شیوه‌ای خلاصه‌تر نسبت به استفاده از سازندهٔ {{domxref("CSSUnitValue.CSSUnitValue", "CSSUnitValue()")}} ایجاد می‌کنند.

## نحو (Syntax)

```js-nolint
CSS.number(number)
CSS.percent(number)

// <length>
CSS.em(number)
CSS.ex(number)
CSS.ch(number)
CSS.ic(number)
CSS.rem(number)
CSS.lh(number)
CSS.rlh(number)
CSS.vw(number)
CSS.vh(number)
CSS.vi(number)
CSS.vb(number)
CSS.vmin(number)
CSS.vmax(number)
CSS.cm(number)
CSS.mm(number)
CSS.Q(number)
CSS.in(number)
CSS.pt(number)
CSS.pc(number)
CSS.px(number)

// <angle>
CSS.deg(number)
CSS.grad(number)
CSS.rad(number)
CSS.turn(number)

// <time>
CSS.s(number)
CSS.ms(number)

// <frequency>
CSS.Hz(number)
CSS.kHz(number)

// <resolution>
CSS.dpi(number)
CSS.dpcm(number)
CSS.dppx(number)

// <flex>
CSS.fr(number)
```

### پارامترها

- `number`
  - : عددی که در مقدار واحد CSS استفاده می‌شود.

### مقدار بازگشتی

یک شیء {{domxref("CSSUnitValue")}} با مقدار عددی و واحد مشخص‌شده.

## مثال‌ها

ما از تابع عددی `CSS.vmax()` برای ایجاد یک {{domxref('CSSUnitValue')}} استفاده می‌کنیم:

```js
const height = CSS.vmax(50);

console.log(height); // CSSUnitValue {value: 50, unit: "vmax"}
console.log(height.value); // 50
console.log(height.unit); // vmax
```

در این مثال، حاشیهٔ (margin) عنصر خود را با استفاده از تابع `CSS.px()` تنظیم می‌کنیم:

```js
myElement.attributeStyleMap.set("margin", CSS.px(40));
const currentMargin = myElement.attributeStyleMap.get("margin");
console.log(currentMargin.value, currentMargin.unit); // 40, 'px'
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("CSSUnitValue.CSSUnitValue", "CSSUnitValue()")}}
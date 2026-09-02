---
title: "MathMLElement: focus() method"
short-title: focus()
slug: Web/API/MathMLElement/focus
page-type: web-api-instance-method
browser-compat: api.MathMLElement.focus
---

{{APIRef("MathML")}}

متد **`focus()`** در رابط {{domxref("MathMLElement")}}، در صورت امکان‌پذیر بودن، تمرکز را روی عنصر MathML مشخص‌شده قرار می‌دهد. عنصر متمرکز، عنصری است که به‌طور پیش‌فرض رویدادهای صفحه‌کلید و مشابه را دریافت می‌کند.

به‌طور پیش‌فرض، مرورگر پس از تمرکز، عنصر را به دید کاربر می‌آورد (اسکرول می‌کند) و ممکن است نشانهٔ بصری نیز برای عنصر متمرکز فراهم کند (معمولاً با نمایش یک «حلقهٔ تمرکز» در اطراف عنصر). گزینه‌های پارامتر برای غیرفعال کردن اسکرول پیش‌فرض و اجبار نمایش نشانهٔ بصری روی عناصر ارائه شده‌اند. اگر `focus()` را از یک کنترل‌کنندهٔ رویداد `mousedown` فراخوانی کنید، باید `event.preventDefault()` را نیز فراخوانی کنید تا تمرکز از `MathMLElement` خارج نشود.

## Syntax

```js-nolint
focus()
focus(options)
```

### Parameters

- `options` {{optional_inline}}
  - : یک شیء برای کنترل جنبه‌های فرایند تمرکز. این شیء ممکن است ویژگی‌های زیر را داشته باشد:
    - `preventScroll` {{optional_inline}}
      - : یک مقدار بولین که نشان می‌دهد آیا مرورگر باید سند را اسکرول کند تا عنصر تازه متمرکز شده به دید کاربر بیاید یا خیر. مقدار `false` برای `preventScroll` (مقدار پیش‌فرض) به این معنی است که مرورگر پس از تمرکز، عنصر را به دید کاربر می‌آورد. اگر `preventScroll` روی `true` تنظیم شود، هیچ اسکرولی رخ نخواهد داد.

### Return value

هیچ ({{jsxref("undefined")}}).

## Examples

### تمرکز روی یک عنصر MathML

این مثال از یک دکمه برای تنظیم تمرکز روی یک عنصر MathML استفاده می‌کند.

#### HTML

```html
<div>
  <math>
    <msup id="myMath" tabindex="0">
      <mi>x</mi>
      <mn>2</mn>
    </msup>
  </math>
  <button id="focusButton">Focus the Math</button>
</div>
```

#### JavaScript

```js
const mathElement = document.getElementById("myMath");

document.getElementById("focusButton").addEventListener("click", () => {
  mathElement.focus();
});
```

### نتیجه

{{EmbedLiveSample("focus",100,100)}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("MathMLElement.blur()")}}
- {{domxref("HTMLElement.focus()")}}
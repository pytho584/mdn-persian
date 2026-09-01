---
title: "CSSStyleDeclaration: item() method"
---

{{ APIRef("CSSOM") }}

متد `CSSStyleDeclaration.item()` یک نام خصوصیت CSS را از یک {{domxref('CSSStyleDeclaration')}} بر اساس ایندکس برمی‌گرداند.

این متد تا زمانی که آرگومان ارائه دهید، استثنا پرتاب نمی‌کند؛ اگر ایندکس خارج از محدوده باشد، رشته خالی برگردانده می‌شود و اگر هیچ آرگومانی ارائه نشود، یک {{jsxref("TypeError")}} پرتاب می‌شود.

## Syntax

```js-nolint
item(index)
```

### Parameters

- `index`
  - : ایندکس گره‌ای که باید دریافت شود. ایندکس از صفر شروع می‌شود.

### Return value

یک رشته که نام خصوصیت CSS در ایندکس مشخص شده است.

جاوااسکریپت یک نحو ساده‌تر ویژه برای دریافت یک آیتم از یک NodeList بر اساس ایندکس دارد:

```js
const propertyName = style[index];
```

### Exceptions

- {{jsxref("TypeError")}}
  - : اگر هیچ آرگومانی ارائه نشود، پرتاب می‌شود.

## Examples

```js
const style = document.getElementById("div1").style;
const propertyName = style.item(1); // یا style[1] - دومین استایل لیست شده را برمی‌گرداند
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}
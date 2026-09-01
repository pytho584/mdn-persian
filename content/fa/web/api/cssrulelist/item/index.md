---
title: "CSSRuleList: item() method"
short-title: item()
slug: Web/API/CSSRuleList/item
page-type: web-api-instance-method
browser-compat: api.CSSRuleList.item
---

{{ APIRef("CSSOM") }}

متود **`item()`** در رابط {{domxref("CSSRuleList")}}، شیء {{domxref("CSSRule")}} را در `index` مشخصشده برمیگرداند، یا اگر `index` موردنظر وجود نداشته باشد، `null` را برمیگرداند.

## Syntax

```js-nolint
item(index)
```

### Parameters

- `index`
  - : یک عدد صحیح.

### Return value

یک {{domxref("CSSRule")}}.

## Examples

در مثال زیر، فرض میکنیم که لیست `myRules` فقط سه آیتم دارد.

```js
let myRules = document.styleSheets[0].cssRules;
console.log(myRules.item(0)); // اولین آیتم CSSRule از این لیست را ثبت میکند

// دسترسی به آیتمهای ناموجود با این متود، null برمیگرداند نه undefined
console.log(myRules.item(5)); // null
console.log(myRules[5]); // undefined
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

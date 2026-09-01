---
title: "CSSKeywordValue: value property"
short-title: value
slug: Web/API/CSSKeywordValue/value
page-type: web-api-instance-property
browser-compat: api.CSSKeywordValue.value
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

ویژگی **`value`** از رابط {{domxref("CSSKeywordValue")}}، کلمهٔ کلیدی را به‌صورت یک رشته نمایش می‌دهد.

## مقدار

یک رشته.

### استثناها

- {{jsxref("TypeError")}}
  - : اگر ویژگی `value` روی یک {{jsxref('String')}} خالی تنظیم شود، این خطا پرتاب می‌شود.

## مثال‌ها

### استفادهٔ پایه

مثال زیر، ویژگی CSS {{cssxref('display')}} را به مقدار پیش‌فرض خود بازنشانی می‌کند.

```js
let indicator = document.getElementById("indicator");
indicator.attributeStyleMap.set("display", new CSSKeywordValue("initial"));
indicator.attributeStyleMap.get("display").value; // 'initial'
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
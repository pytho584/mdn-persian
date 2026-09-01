---
title: "CSSStyleDeclaration: removeProperty() method"
---

---
title: "CSSStyleDeclaration: removeProperty() method"
short-title: removeProperty()
slug: Web/API/CSSStyleDeclaration/removeProperty
page-type: web-api-instance-method
browser-compat: api.CSSStyleDeclaration.removeProperty
---

{{ APIRef("CSSOM") }}

متد **`CSSStyleDeclaration.removeProperty()`** یک ویژگی را از شیء اعلان سبک CSS حذف می‌کند.

## نحو

```js-nolint
removeProperty(property)
```

### پارامترها

- `property`
  - : رشته‌ای است که نام ویژگی موردنظر برای حذف را نشان می‌دهد. نام ویژگی‌های چندکلمه‌ای به صورت خط تیره‌دار ({{Glossary("kebab_case", "kebab-case")}}) هستند و نه به صورت {{Glossary("camel_case", "camel-cased")}}.

### مقدار بازگشتی

رشته‌ای برابر با مقدار ویژگی CSS قبل از حذف شدن.

### استثناها

- `NoModificationAllowedError` {{domxref('DOMException')}}
  - : زمانی پرتاب می‌شود که ویژگی یا بلوک اعلان فقط‌خواندنی باشد.

## مثال‌ها

کد جاوااسکریپت زیر ویژگی CSS به نام `background-color` را از یک قانون انتخابگر حذف می‌کند:

```js
const declaration = document.styleSheets[0].rules[0].style;
const oldValue = declaration.removeProperty("background-color");
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
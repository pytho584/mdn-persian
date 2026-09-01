---
title: "Highlight: values() method"
---

---
title: "Highlight: values() method"
short-title: values()
slug: Web/API/Highlight/values
page-type: web-api-instance-method
browser-compat: api.Highlight.values
spec-urls: https://tc39.es/ecma262/multipage/keyed-collections.html#sec-set.prototype.values
---

{{APIRef("CSS Custom Highlight API")}}

متد **`values()`** از رابط {{domxref("Highlight")}} یک شیء [Iterator](/en-US/docs/Web/JavaScript/Guide/Iterators_and_generators) جدید برمی‌گرداند که شامل مقادیر هر شیء `AbstractRange` در شیء `Highlight` به ترتیب درج است.

> [!NOTE]
> متد **`keys()`** یک نام مستعار برای این متد است. رفتار آن دقیقاً یکسان است و **مقادیر** عناصر `Highlight` را برمی‌گرداند.

`Highlight` یک شیء شبیه به {{jsxref("Set")}} است، بنابراین این کار مشابه استفاده از {{jsxref("Set.values()")}} است.

## نحو

```js-nolint
values()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک شیء تکرارگر جدید که هر شیء `AbstractRange` را در `Highlight` داده‌شده، به ترتیب درج، در بر می‌گیرد.

## مثال‌ها

قطعه کد زیر نحوه ایجاد یک شیء `Highlight` جدید با سه شیء `AbstractRange` و استفاده از تکرارگر برگشتی از متد `values()` برای ثبت کردن این سه محدوده را نشان می‌دهد:

```js
const myHighlight = new Highlight();
myHighlight.add(new Range());
myHighlight.add(new Range());
myHighlight.add(new Range());

const iter = myHighlight.values();

for (value of iter) {
  console.log(value); // Range
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("css_custom_highlight_api", "The CSS Custom Highlight API", "", "nocode")}}
- [CSS Custom Highlight API: The Future of Highlighting Text Ranges on the Web](https://css-tricks.com/css-custom-highlight-api-early-look/)
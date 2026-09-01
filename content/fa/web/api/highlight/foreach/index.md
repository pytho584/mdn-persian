---
title: "Highlight: forEach() method"
short-title: forEach()
slug: Web/API/Highlight/forEach
page-type: web-api-instance-method
browser-compat: api.Highlight.forEach
spec-urls: https://tc39.es/ecma262/multipage/keyed-collections.html#sec-set.prototype.foreach
---

{{APIRef("CSS Custom Highlight API")}}

متد **`forEach()`** در接口 {{domxref("Highlight")}} یک تابع داده‌شده را یک‌بار برای هر شیء {{domxref("AbstractRange")}} در شیء `Highlight`، به ترتیب درج، اجرا می‌کند.

`Highlight` یک شیء شبیه به {{jsxref("Set")}} است، بنابراین این متد مشابه استفاده از {{jsxref("Set.forEach()")}} است.

## نحو (Syntax)

```js-nolint
forEach(callbackFn)
forEach(callbackFn, thisArg)
```

### پارامترها

- `callback`
  - : تابعی که برای هر شیء `AbstractRange` اجرا می‌شود و سه آرگومان می‌گیرد:
    - `range`, `key`
      - : شیء `AbstractRange` فعلی که در `Highlight` پردازش می‌شود. از آنجا که در `Highlight` کلیدی وجود ندارد، `range` برای هر دو آرگومان ارسال می‌شود.
    - `highlight`
      - : شیء `Highlight` که `forEach()` روی آن فراخوانی شده است.

- `thisArg`
  - : مقداری که به‌عنوان `this` هنگام اجرای `callbackFn` استفاده می‌شود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

قطعه کد زیر نحوه ایجاد یک هایلایت جدید با دو بازه و سپس ثبت (log) بازه‌ها با استفاده از متد `forEach()` را نشان می‌دهد:

```js
function logRanges(range, key, highlight) {
  console.log(`Highlight object ${highlight} contains range ${range}`);
}

const text = new Text("Time is an illusion. Lunchtime doubly so.");

const range1 = document.createRange();
range1.setStart(text, 0);
range1.setEnd(text, 4);

const range2 = document.createRange();
range2.setStart(text, 21);
range2.setEnd(text, 30);

const myHighlight = new Highlight();
myHighlight.add(range1);
myHighlight.add(range2);

myHighlight.forEach(logRanges);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("css_custom_highlight_api", "The CSS Custom Highlight API", "", "nocode")}}
- [CSS Custom Highlight API: The Future of Highlighting Text Ranges on the Web](https://css-tricks.com/css-custom-highlight-api-early-look/)
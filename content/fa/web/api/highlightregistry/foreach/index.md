---
title: "HighlightRegistry: forEach() method"
---

---
title: "HighlightRegistry: forEach() method"
short-title: forEach()
slug: Web/API/HighlightRegistry/forEach
page-type: web-api-instance-method
browser-compat: api.HighlightRegistry.forEach
spec-urls: https://tc39.es/ecma262/multipage/keyed-collections.html#sec-map.prototype.foreach
---

{{APIRef("CSS Custom Highlight API")}}

متد **`forEach()`** در رابط {{domxref("HighlightRegistry")}}، یک تابع ارائه‌شده را یک‌بار برای هر شیء {{domxref("Highlight")}} در رجیستری، به ترتیب درج، اجرا می‌کند.

`HighlightRegistry` یک شیء شبیه به {{jsxref("Map")}} است، بنابراین این کار مشابه استفاده از {{jsxref("Map.forEach()")}} است.

## نحو

```js-nolint
forEach(callbackFn)
forEach(callbackFn, thisArg)
```

### پارامترها

- `callback`
  - : تابعی که برای هر شیء `Highlight` اجرا می‌شود و سه آرگومان می‌گیرد:
    - `highlight`
      - : هایلایت کنونی.
    - `name`
      - : نام هایلایت.
    - `registry`
      - : شیء رجیستری که `forEach()` روی آن فراخوانی شده است.

- `thisArg`
  - : مقداری که هنگام اجرای `callbackFn` به‌عنوان `this` استفاده می‌شود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

قطعه کد زیر نحوه ایجاد یک هایلایت جدید با دو بازه و سپس ثبت این بازه‌ها در خروجی را با استفاده از متد `forEach()` نشان می‌دهد:

```js
function logAllHighlights(highlight, name) {
  console.log(`Highlight ${name} exists in the registry`, highlight);
}

const customHighlight1 = new Highlight();
const customHighlight2 = new Highlight();
const customHighlight3 = new Highlight();

CSS.highlights.set("custom-highlight-1", customHighlight1);
CSS.highlights.set("custom-highlight-2", customHighlight2);
CSS.highlights.set("custom-highlight-3", customHighlight3);

CSS.highlights.forEach(logAllHighlights);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("css_custom_highlight_api", "The CSS Custom Highlight API", "", "nocode")}}
- [CSS Custom Highlight API: The Future of Highlighting Text Ranges on the Web](https://css-tricks.com/css-custom-highlight-api-early-look/)
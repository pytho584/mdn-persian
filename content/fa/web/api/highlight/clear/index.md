---
title: "Highlight: clear() method"
---

{{APIRef("CSS Custom Highlight API")}}

متد **`clear()`** از رابط {{domxref("Highlight")}} همهٔ اشیاء {{domxref("AbstractRange")}} را از یک شیء `Highlight` حذف می‌کند.

`Highlight` یک شیء شبیه به {{jsxref("Set")}} است، بنابراین این کار مشابه استفاده از {{jsxref("Set.clear()")}} است.

## نحو (Syntax)

```js-nolint
clear()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

قطعه‌کد زیر نحوهٔ ایجاد یک هایلایت جدید با دو بازه و سپس پاک کردن آن را نشان می‌دهد:

```js
const highlight = new Highlight(range1, range2);
console.log(highlight.size); // 2

highlight.clear();
console.log(highlight.size); // 0
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("css_custom_highlight_api", "The CSS Custom Highlight API", "", "nocode")}}
- [CSS Custom Highlight API: The Future of Highlighting Text Ranges on the Web](https://css-tricks.com/css-custom-highlight-api-early-look/)
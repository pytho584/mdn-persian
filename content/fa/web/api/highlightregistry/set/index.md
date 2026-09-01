---
title: "HighlightRegistry: set() method"
short-title: set()
slug: Web/API/HighlightRegistry/set
page-type: web-api-instance-method
browser-compat: api.HighlightRegistry.set
spec-urls: https://tc39.es/ecma262/multipage/keyed-collections.html#sec-map.prototype.set
---

{{APIRef("CSS Custom Highlight API")}}

متد **`set()`** از رابط {{domxref("HighlightRegistry")}} یک شیء {{domxref("Highlight")}} را با نام مشخص‌شده به رجیستری اضافه یا آن را به‌روزرسانی می‌کند.

`HighlightRegistry` یک شیء شبیه به {{jsxref("Map")}} است، بنابراین این روش مشابه استفاده از {{jsxref("Map.set()")}} است.

## نحو (Syntax)

```js-nolint
set(name, highlight)
```

### پارامترها

- `name`
  - : نام شیء `Highlight` برای افزودن یا به‌روزرسانی. نام باید یک {{jsxref("String")}} باشد.
- `highlight`
  - : شیء `Highlight` برای افزودن یا به‌روزرسانی. این باید یک نمونه از رابط {{domxref("Highlight")}} باشد.

### مقدار بازگشتی

شیء `HighlightRegistry`.

## مثال‌ها

### استفاده از set()

```js
const fooHighlight = new Highlight();
CSS.highlights.set("foo", fooHighlight);
```

### استفاده از set() با زنجیره‌سازی

از آنجا که متد `set()` خودِ رجیستری را برمی‌گرداند، می‌توانید فراخوانی متد را مانند زیر زنجیره‌ای کنید:

```js
const fooHighlight = new Highlight();
const barHighlight = new Highlight();
const bazHighlight = new Highlight();

CSS.highlights
  .set("foo", fooHighlight)
  .set("bar", barHighlight)
  .set("baz", bazHighlight);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("css_custom_highlight_api", "The CSS Custom Highlight API", "", "nocode")}}
- ماژول [CSS custom highlight API](/en-US/docs/Web/CSS/Guides/Custom_highlight_API)
- [CSS Custom Highlight API: The Future of Highlighting Text Ranges on the Web](https://css-tricks.com/css-custom-highlight-api-early-look/)
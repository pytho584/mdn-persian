---
title: "Highlight: Highlight() constructor"
short-title: Highlight()
slug: Web/API/Highlight/Highlight
page-type: web-api-constructor
browser-compat: api.Highlight.Highlight
---

{{APIRef("CSS Custom Highlight API")}}

سازندهٔ **`Highlight()`** یک شیء {{domxref("Highlight")}} جدید ایجاد می‌کند که می‌تواند مجموعه‌ای از اشیاء {{domxref("AbstractRange")}} را در خود نگه دارد تا با استفاده از {{domxref("css_custom_highlight_api", "CSS Custom Highlight API", "", "nocode")}} style دهی شوند.

## Syntax

```js-nolint
new Highlight()
new Highlight(range)
new Highlight(range1, range2, /* …, */ rangeN)
```

### Parameters

- `range1`, …, `rangeN` {{optional_inline}}
  - : یک یا چند شیء {{domxref("AbstractRange")}} اولیه که به هایلایت جدید اضافه می‌شوند.

### Return value

یک شیء `Highlight` جدید.

## Examples

کد نمونهٔ زیر نحوهٔ ایجاد یک شیء هایلایت خالی و سپس افزودن rangeها به آن را نشان می‌دهد:

```js
const highlight = new Highlight();
highlight.add(range1);
highlight.add(range2);
```

کد نمونهٔ زیر نحوهٔ ایجاد یک شیء هایلایت جدید و افزودن rangeها به آن در هنگام نمونه‌سازی را نشان می‌دهد:

```js
const highlight = new Highlight(range1, range2);
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("css_custom_highlight_api", "The CSS Custom Highlight API", "", "nocode")}}
- [CSS custom highlight API](/en-US/docs/Web/CSS/Guides/Custom_highlight_API) module
- [CSS Custom Highlight API: The Future of Highlighting Text Ranges on the Web](https://css-tricks.com/css-custom-highlight-api-early-look/)
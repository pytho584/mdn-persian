---
title: "CSS: highlights static property"
short-title: highlights
slug: Web/API/CSS/highlights_static
page-type: web-api-static-property
browser-compat: api.CSS.highlights_static
---

{{APIRef("CSSOM")}}

ویژگی استاتیک و فقط‑خواندنی **`highlights`** از واسط {{domxref("CSS")}} دسترسی به `HighlightRegistry` را فراهم می‌کند که برای سبک‌دهی به بازه‌های متنی دلخواه با استفاده از {{domxref("css_custom_highlight_api", "CSS Custom Highlight API", "", "nocode")}} به کار می‌رود.

## مقدار

شی {{DOMxRef("HighlightRegistry")}}.

## مثال‌ها

مثال زیر نحوه ایجاد چندین بازه متنی، ساختن یک شی `Highlight` برای آن‌ها، ثبت این برجسته‌سازی در `HighlightRegistry` و در نهایت سبک‌دهی به بازه‌های متنی با استفاده از شبه‑عنصر {{cssxref("::highlight", "::highlight()")}} را نشان می‌دهد.

```js
const parentNode = document.getElementById("foo");

const range1 = new Range();
range1.setStart(parentNode, 10);
range1.setEnd(parentNode, 20);

const range2 = new Range();
range2.setStart(parentNode, 40);
range2.setEnd(parentNode, 60);

const myCustomHighlight = new Highlight(range1, range2);

CSS.highlights.set("my-custom-highlight", myCustomHighlight);
```

```css
::highlight(my-custom-highlight) {
  background-color: yellow;
  color: black;
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("css_custom_highlight_api", "CSS Custom Highlight API", "", "nocode")}}
- ماژول [CSS custom highlight API](/en-US/docs/Web/CSS/Guides/Custom_highlight_API)
- [CSS Custom Highlight API: The Future of Highlighting Text Ranges on the Web](https://css-tricks.com/css-custom-highlight-api-early-look/)
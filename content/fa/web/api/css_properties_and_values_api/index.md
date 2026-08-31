---
title: CSS Properties and Values API
slug: Web/API/CSS_Properties_and_Values_API
page-type: web-api-overview
browser-compat:
  - api.CSSPropertyRule
  - api.CSS.registerProperty_static
---

{{DefaultAPISidebar("CSS Properties and Values API")}}

**CSS Properties and Values API** — بخشی از مجموعه‌ی [CSS Houdini](/en-US/docs/Web/API/Houdini_APIs) — به توسعه‌دهندگان امکان می‌دهد تا [ویژگی‌های سفارشی CSS](/en-US/docs/Web/CSS/Reference/Properties/--*) خود را به‌صراحت تعریف کنند؛ این امر بررسی نوع ویژگی، مقادیر پیش‌فرض، و ویژگی‌هایی که مقدار خود را به ارث می‌برند یا نمی‌برند را ممکن می‌سازد.

## رابط‌ها

- {{domxref('CSS/registerProperty_static', 'CSS.registerProperty')}}
  - : نحوه‌ی تفسیر [ویژگی‌های سفارشی CSS](/en-US/docs/Web/CSS/Reference/Properties/--*) توسط مرورگر را تعریف می‌کند. از طریق {{domxref('CSS/registerProperty_static', 'CSS.registerProperty')}} در [جاوااسکریپت](/en-US/docs/Web/JavaScript) به این رابط دسترسی پیدا کنید.
- {{cssxref('@property')}}
  - : نحوه‌ی تفسیر [ویژگی‌های سفارشی CSS](/en-US/docs/Web/CSS/Reference/Properties/--*) توسط مرورگر را تعریف می‌کند. از طریق [قاعده‌ی at-rule](/en-US/docs/Web/CSS/Guides/Syntax/At-rules) به نام {{cssxref('@property')}} در [CSS](/en-US/docs/Web/CSS) به این رابط دسترسی پیدا کنید.

## مثال‌ها

در مثال زیر، یک [ویژگی سفارشی](/en-US/docs/Web/CSS/Reference/Properties/--*) به نام `--my-color` با استفاده از {{domxref('CSS/registerProperty_static', 'CSS.registerProperty')}} در [جاوااسکریپت](/en-US/docs/Web/JavaScript) ثبت می‌شود. `--my-color` از نحو رنگ CSS استفاده می‌کند، مقدار پیش‌فرض آن `#c0ffee` خواهد بود و مقدار خود را به ارث نمی‌برد:

```js
window.CSS.registerProperty({
  name: "--my-color",
  syntax: "<color>",
  inherits: false,
  initialValue: "#c0ffee",
});
```

همین ثبت را می‌توان در [CSS](/en-US/docs/Web/CSS) با استفاده از [قاعده‌ی at-rule](/en-US/docs/Web/CSS/Guides/Syntax/At-rules) به نام {{cssxref('@property')}} انجام داد:

```css
@property --my-color {
  syntax: "<color>";
  inherits: false;
  initial-value: #c0ffee;
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از API ویژگی‌ها و مقادیر CSS](/en-US/docs/Web/API/CSS_Properties_and_Values_API/guide)
- [CSS Painting API](/en-US/docs/Web/API/CSS_Painting_API)
- [CSS Typed Object Model](/en-US/docs/Web/API/CSS_Typed_OM_API)
- [Houdini APIs](/en-US/docs/Web/API/Houdini_APIs)
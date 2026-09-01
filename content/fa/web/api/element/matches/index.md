---
title: "Element: matches() method"
short-title: matches()
slug: Web/API/Element/matches
page-type: web-api-instance-method
browser-compat: api.Element.matches
---

{{APIRef("DOM")}}

متد **`matches()`** از رابط {{domxref("Element")}} بررسی می‌کند که آیا عنصر توسط [CSS selector](/en-US/docs/Learn_web_development/Core/Styling_basics/Basic_selectors) مشخص‌شده انتخاب می‌شود یا خیر.

## Syntax

```js-nolint
matches(selectors)
```

### Parameters

- `selectors`
  - : یک رشته حاوی [CSS selectors](/en-US/docs/Learn_web_development/Core/Styling_basics/Basic_selectors) معتبر برای آزمایش {{domxref("Element")}} در برابر آن.

### Return value

`true` اگر {{domxref("Element")}} با `selectors` مطابقت داشته باشد. در غیر این صورت `false`.

### Exceptions

- `SyntaxError` {{domxref("DOMException")}}
  - : اگر `selectors` نتواند به عنوان یک لیست انتخاب‌گر CSS تجزیه شود، پرتاب می‌شود.

## Examples

### HTML

```html
<ul id="birds">
  <li>Orange-winged parrot</li>
  <li class="endangered">Philippine eagle</li>
  <li>Great white pelican</li>
</ul>
```

### JavaScript

```js
const birds = document.querySelectorAll("li");

for (const bird of birds) {
  if (bird.matches(".endangered")) {
    console.log(`The ${bird.textContent} is endangered!`);
  }
}
```

این کد عبارت "The Philippine eagle is endangered!" را در کنسول ثبت می‌کند، زیرا عنصر دارای یک ویژگی `class` با مقدار `endangered` است.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- ماژول [CSS selectors](/en-US/docs/Web/CSS/Guides/Selectors)
- سایر متدهای {{domxref("Element")}} که انتخاب‌گر می‌گیرند: {{domxref("Element.querySelector()")}}, {{domxref("Element.querySelectorAll()")}}, و {{domxref("element.closest()")}}.
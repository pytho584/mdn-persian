---
title: "Element: ariaCurrent property"
short-title: ariaCurrent
slug: Web/API/Element/ariaCurrent
page-type: web-api-instance-property
browser-compat: api.Element.ariaCurrent
---

{{APIRef("DOM")}}

خاصیت **`ariaCurrent`** از رابط {{domxref("Element")}} مقدار ویژگی [`aria-current`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-current) را منعکس می‌کند. این ویژگی نشان‌دهنده عنصری است که آیتم جاری را درون یک ظرف یا مجموعه‌ای از عناصر مرتبط مشخص می‌کند.

## مقدار

یک رشته (string) با یکی از مقادیر زیر:

- `"page"`
  - : نمایانگر صفحه جاری درون مجموعه‌ای از صفحات است.
- `"step"`
  - : نمایانگر گام جاری درون یک فرایند است.
- `"location"`
  - : نمایانگر مکان جاری است، برای مثال صفحه جاری در سلسله‌مراتب خرده‌نان (breadcrumbs).
- `"date"`
  - : نمایانگر تاریخ جاری درون مجموعه‌ای از تاریخ‌ها است.
- `"time"`
  - : نمایانگر زمان جاری درون مجموعه‌ای از زمان‌ها است.
- `"true"`
  - : نمایانگر آیتم جاری درون یک مجموعه است.
- `"false"`
  - : نمایانگر آیتم جاری درون یک مجموعه نیست.

## مثال‌ها

در این مثال، مجموعه‌ای از پیوندها برای پیمایش سایت استفاده شده‌اند. ویژگی `aria-current` صفحه جاری را مشخص می‌کند. مقدار `page` در اعلام screen reader گنجانده می‌شود. با استفاده از `ariaCurrent` می‌توانیم آن مقدار را به‌روز کنیم.

```html
<nav>
  <ul>
    <li><a id="link-home" href="/" aria-current="page">خانه</a></li>
    <li><a href="/">درباره</a></li>
    <li><a href="/">تماس</a></li>
  </ul>
</nav>
```

```js
let el = document.getElementById("link-home");
console.log(el.ariaCurrent); // "page"
el.ariaCurrent = "tab";
console.log(el.ariaCurrent); // "tab"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [استفاده از ویژگی aria-current](https://tink.uk/using-the-aria-current-attribute/)
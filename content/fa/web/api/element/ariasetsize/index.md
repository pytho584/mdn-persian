---
title: "Element: ariaSetSize property"
short-title: ariaSetSize
slug: Web/API/Element/ariaSetSize
page-type: web-api-instance-property
browser-compat: api.Element.ariaSetSize
---

{{APIRef("DOM")}}

ویژگی **`ariaSetSize`** از رابط {{domxref("Element")}} مقدار مشخصهٔ [`aria-setsize`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-setsize) را بازتاب می‌دهد؛ این مشخصه، تعداد آیتم‌ها را در مجموعهٔ فعلی از آیتم‌های فهرست (listitems) یا آیتم‌های درخت (treeitems) تعریف می‌کند.

## مقدار

یک رشته حاوی یک عدد صحیح.

## مثال‌ها

در این مثال، مشخصهٔ `aria-setsize` روی عنصری با شناسهٔ `tab-id` به "3" تنظیم شده است تا به دستگاه اطلاع دهد که در حال حاضر ۳ تب در گروه وجود دارد. با استفاده از `ariaSetSize`، مقدار را به "4" به‌روزرسانی می‌کنیم.

```html
<button
  role="tab"
  aria-selected="true"
  aria-setsize="3"
  aria-controls="tabpanel-id"
  id="tab-id">
  Tab label
</button>
```

```js
let el = document.getElementById("tab-id");
console.log(el.ariaSetSize); // 3
el.ariaSetSize = "4";
console.log(el.ariaSetSize); // 4
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [ARIA: tab role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role)
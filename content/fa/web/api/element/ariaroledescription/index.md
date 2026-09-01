---
title: "Element: ariaRoleDescription property"
---

---
title: "Element: ariaRoleDescription property"
short-title: ariaRoleDescription
slug: Web/API/Element/ariaRoleDescription
page-type: web-api-instance-property
browser-compat: api.Element.ariaRoleDescription
---

{{APIRef("DOM")}}

ویژگی **`ariaRoleDescription`** در رابط {{domxref("Element")}} مقدار ویژگی [`aria-roledescription`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-roledescription) را منعکس می‌کند؛ ویژگی‌ای که توصیفی قابل‌خواندن برای انسان و بومی‌شده توسط نویسنده را برای نقش یک عنصر تعریف می‌کند.

## مقدار

یک رشته (string).

## مثال‌ها

در این مثال، ویژگی `aria-roledescription` روی عنصری با شناسه (ID) «myApplication» تنظیم شده است. با استفاده از `ariaRoleDescription` می‌توانیم مقدار آن را به‌روزرسانی کنیم.

```html
<div
  id="myApplication"
  role="application"
  aria-roledescription="a description of this widget">
  …
</div>
```

```js
let el = document.getElementById("myApplication");
console.log(el.ariaRoleDescription); // "a description of this widget"
el.ariaRoleDescription = "an updated description of this widget";
console.log(el.ariaRoleDescription); // "an updated description of this widget"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- [ARIA: application role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/application_role)

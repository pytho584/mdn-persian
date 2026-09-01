---
title: "Element: removeAttribute() method"
---

---
title: "Element: removeAttribute() method"
short-title: removeAttribute()
slug: Web/API/Element/removeAttribute
page-type: web-api-instance-method
browser-compat: api.Element.removeAttribute
---

{{ APIRef("DOM") }}

متد **`removeAttribute()`** در {{domxref("Element")}} ویژگی‌ای با نام مشخص‌شده را از عنصر حذف می‌کند.

## نحو

```js-nolint
removeAttribute(attrName)
```

### پارامترها

- `attrName`
  - : رشته‌ای که نام ویژگی‌ای را که باید از عنصر حذف شود مشخص می‌کند. اگر ویژگی موردنظر وجود نداشته باشد، `removeAttribute()` بدون ایجاد خطا بازمی‌گردد.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## نکات استفاده

بهتر است به‌جای تنظیم مقدار ویژگی روی `null`، چه به‌طور مستقیم و چه با استفاده از {{domxref("Element.setAttribute", "setAttribute()")}}، از `removeAttribute()` استفاده کنید. بسیاری از ویژگی‌ها اگر روی `null` تنظیم شوند، آن‌طور که انتظار می‌رود رفتار نخواهند کرد.

## مثال‌ها

```js
// Given: <div id="div1" disabled width="200px">
document.getElementById("div1").removeAttribute("disabled");
// Now: <div id="div1" width="200px">
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.hasAttribute()")}}
- {{domxref("Element.getAttribute()")}}
- {{domxref("Element.setAttribute()")}}
- {{domxref("Element.toggleAttribute()")}}
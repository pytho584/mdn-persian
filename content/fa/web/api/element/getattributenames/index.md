---
title: "Element: getAttributeNames() method"
short-title: getAttributeNames()
slug: Web/API/Element/getAttributeNames
page-type: web-api-instance-method
browser-compat: api.Element.getAttributeNames
---

متد **`getAttributeNames()`** در رابط {{domxref("Element")}} نام ویژگی‌های عنصر را به‌صورت یک {{jsxref("Array")}} از رشته‌ها برمی‌گرداند. اگر عنصر هیچ ویژگی‌ای نداشته باشد، یک آرایهٔ خالی برمی‌گرداند.

استفاده از `getAttributeNames()` در کنار {{domxref("Element.getAttribute","getAttribute()")}} جایگزینی کارآمد از نظر حافظه و با کارایی بالا برای دسترسی به {{domxref("Element.attributes")}} است.

نام‌هایی که توسط `getAttributeNames()` بازگردانده می‌شوند، _نام‌های ویژگی واجد شرایط_ هستند؛ یعنی ویژگی‌هایی که پیشوند فضای نام دارند، نامشان با همان پیشوند فضای نام (و نه خود فضای نام) و به دنبال آن دونقطه و سپس نام ویژگی بازگردانده می‌شود (مثلاً **`xlink:href`**)؛ در حالی که ویژگی‌هایی که پیشوند فضای نام ندارند، نامشان بدون تغییر بازگردانده می‌شود (مثلاً **`href`**).

## نحو (Syntax)

```js-nolint
getAttributeNames()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک ({{jsxref("Array")}}) از رشته‌ها.

## مثال‌ها

مثال زیر نشان می‌دهد که:

- برای ویژگی‌ای که پیشوند فضای نام دارد، `getAttributeNames()` آن پیشوند را همراه با نام ویژگی برمی‌گرداند.
- برای ویژگی‌ای که پیشوند فضای نام ندارد، `getAttributeNames()` فقط نام ویژگی را بدون تغییر برمی‌گرداند.

درک این نکات مهم است:

1. یک ویژگی می‌تواند در DOM با فضای نام حضور داشته باشد اما پیشوند فضای نام نداشته باشد.
2. برای ویژگی‌ای در DOM که فضای نام دارد اما پیشوند فضای نام ندارد، `getAttributeNames()` فقط نام ویژگی را برمی‌گرداند و هیچ اشاره‌ای به این نمی‌کند که ویژگی در یک فضای نام قرار دارد.

مثال زیر شامل چنین حالتی است که «دارای فضای نام اما بدون پیشوند فضای نام» است.

```js
const element = document.createElement("a");

// set "href" attribute with no namespace and no namespace prefix
element.setAttribute("href", "https://example.com");
// set "href" attribute with namespace and also "xlink" namespace prefix
element.setAttributeNS(
  "http://www.w3.org/1999/xlink",
  "xlink:href",
  "https://example.com",
);
// set "show" attribute with namespace but no namespace prefix
element.setAttributeNS("http://www.w3.org/1999/xlink", "show", "new");

// Iterate over element's attributes
for (const name of element.getAttributeNames()) {
  const value = element.getAttribute(name);
  console.log(name, value);
}

// logs:
// href https://example.com
// xlink:href https://example.com
// show new
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
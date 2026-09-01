---
title: "HTMLLinkElement: sheet property"
short-title: sheet
slug: Web/API/HTMLLinkElement/sheet
page-type: web-api-instance-property
browser-compat: api.HTMLLinkElement.sheet
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`sheet`** در رابط {{domxref("HTMLLinkElement")}} شامل شیء stylesheet مرتبط با آن عنصر است.

یک stylesheet با یک `HTMLLinkElement` مرتبط می‌شود اگر برای `<link>` از `rel="stylesheet"` استفاده شود.

## مقدار

یک شیء {{DOMxRef("StyleSheet")}}، یا اگر هیچ شیوه‌نامه‌ای با عنصر مرتبط نباشد، مقدار `null` برمی‌گرداند.

## مثال‌ها

```html
<link rel="stylesheet" href="styles.css" />
```

ویژگی `sheet` در شیء `HTMLLinkElement`، شیء {{domxref("StyleSheet")}} مربوط به `styles.css` را برمی‌گرداند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
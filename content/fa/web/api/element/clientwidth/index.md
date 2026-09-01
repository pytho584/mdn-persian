---
title: "Element: clientWidth property"
short-title: clientWidth
slug: Web/API/Element/clientWidth
page-type: web-api-instance-property
browser-compat: api.Element.clientWidth
---

{{APIRef("DOM")}}

خاصیت فقط-خواندنی **`clientWidth`** در رابط {{domxref("Element")}} برای عناصر درون‌خطی (inline) و عناصر بدون CSS برابر صفر است؛ در غیر این صورت، عرض داخلی یک عنصر را بر حسب پیکسل برمی‌گرداند. این مقدار شامل padding (حاشیه داخلی) می‌شود، اما border (حاشیه)، margin (حاشیه خارجی)، و نوار پیمایش عمودی (در صورت وجود) را شامل نمی‌شود.

هنگامی که `clientWidth` روی عنصر ریشه (عنصر `<html>`) (یا روی `<body>` اگر سند در حالت quirks mode باشد) استفاده شود، عرض viewport (به استثنای هر نوار پیمایش) بازگردانده می‌شود.

## مقدار

یک عدد صحیح.

## مثال‌ها

![An example element with large padding, border and margin. clientWidth is the inner width of the element including its padding, and excluding its margin, border, and vertical scrollbar.](dimensions-client.png)

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [تعیین ابعاد عناصر](/en-US/docs/Web/API/CSS_Object_Model/Determining_the_dimensions_of_elements)
- {{domxref("HTMLElement.offsetWidth")}}
- {{domxref("Element.scrollWidth")}}
- {{domxref("Element.clientHeight")}}
- {{domxref("Element.clientLeft")}}
- {{domxref("Element.clientTop")}}
- {{domxref("Element.getBoundingClientRect()")}}
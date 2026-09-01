---
title: "Element: clientHeight property"
short-title: clientHeight
slug: Web/API/Element/clientHeight
page-type: web-api-instance-property
browser-compat: api.Element.clientHeight
---

{{APIRef("DOM")}}

ویژگی فقط‌خواندنی **`clientHeight``** در رابط {{domxref("Element")}} برای عناصری که جعبه‌ی چیدمان CSS یا درون‌خطی (inline) ندارند، صفر است؛ در غیر این صورت، ارتفاع داخلی عنصر را بر حسب پیکسل برمی‌گرداند. این مقدار شامل padding می‌شود اما borderها، marginها و نوار اسکرroll افقی (در صورت وجود) را شامل نمی‌شود.

`clientHeight` را می‌توان این‌گونه محاسبه کرد: `height` + `padding` در CSS - ارتفاع نوار اسکرroll افقی (در صورت وجود).

وقتی `clientHeight` روی عنصر ریشه (عنصر `<html>`) استفاده شود (یا روی `<body>` اگر سند در حالت quirks باشد)، ارتفاع viewport (بدون احتساب هر نوار اسکرroll) برگردانده می‌شود.

## مقدار

یک عدد صحیح.

## مثال‌ها

![چگونه ویژگی clientHeight ارتفاع داخلی یک عنصر را با در نظر گرفتن height و padding تعیین می‌کند](dimensions-client.png)

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [تعیین ابعاد عناصر](/en-US/docs/Web/API/CSS_Object_Model/Determining_the_dimensions_of_elements)
- {{domxref("HTMLElement.offsetHeight")}}
- {{domxref("Element.scrollHeight")}}
- {{domxref("Element.clientWidth")}}
- {{domxref("Element.clientLeft")}}
- {{domxref("Element.clientTop")}}
- {{domxref("Element.getBoundingClientRect()")}}
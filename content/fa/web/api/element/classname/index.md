---
title: "Element: className property"
short-title: className
slug: Web/API/Element/className
page-type: web-api-instance-property
browser-compat: api.Element.className
---

{{APIRef("DOM")}}

ویژگی **`className`** در رابط {{domxref("Element")}}، مقدار [`ویژگی class`](/en-US/docs/Web/HTML/Reference/Global_attributes/class) عنصر مشخص‌شده را دریافت و تنظیم می‌کند.

## مقدار

یک متغیر رشته‌ای که کلاس یا کلاس‌های جدا شده با فاصله عنصر فعلی را نشان می‌دهد.

## مثال‌ها

```js
const el = document.getElementById("item");
el.className = el.className === "active" ? "inactive" : "active";
```

## نکات

نام `className` به‌جای `class` برای این ویژگی استفاده می‌شود، زیرا در بسیاری از زبان‌هایی که برای دستکاری DOM استفاده می‌شوند، با کلمه کلیدی «class» تداخل دارد.

اگر `element` یک {{domxref("SVGElement")}} باشد، `className` همچنین می‌تواند یک نمونه از {{domxref("SVGAnimatedString")}} باشد. اگر با عناصر SVG کار می‌کنید، تنظیم و دریافت ویژگی `class` عنصر با استفاده از {{domxref("Element.getAttribute")}} و {{domxref("Element.setAttribute")}} آسان‌تر است. با این حال، توجه داشته باشید که {{domxref("Element.getAttribute")}} اگر عنصر دارای [`ویژگی class`](/en-US/docs/Web/HTML/Reference/Global_attributes/class) خالی باشد، به‌جای `""` مقدار [`null`](/en-US/docs/Web/JavaScript/Reference/Operators/null) برمی‌گرداند.

```js
elm.setAttribute("class", "my-class");
const myClass = elm.getAttribute("class");
```

> [!NOTE]
> `class` نام یک **ویژگی HTML (HTML Attribute)** است، در حالی که `className` نام یک **ویژگی DOM (DOM Property)** است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("element.classList")}}
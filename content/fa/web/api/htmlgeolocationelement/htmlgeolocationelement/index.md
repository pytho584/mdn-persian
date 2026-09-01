---
title: "HTMLGeolocationElement: HTMLGeolocationElement() constructor"
short-title: HTMLGeolocationElement()
slug: Web/API/HTMLGeolocationElement/HTMLGeolocationElement
page-type: web-api-constructor
status:
  - experimental
browser-compat: api.HTMLGeolocationElement.HTMLGeolocationElement
---

{{APIRef("HTML DOM")}}{{SeeCompatTable}}

سازندهٔ **`HTMLGeolocationElement()`** یک نمونهٔ جدید از شیء {{domxref("HTMLGeolocationElement")}} می‌سازد.

## نحو (Syntax)

```js-nolint
new HTMLGeolocationElement()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک نمونهٔ جدید از شیء {{domxref("HTMLGeolocationElement")}}، اگر به‌صورت داخلی توسط مرورگر استفاده شود.

توسعه‌دهندگان نمی‌توانند مستقیماً از سازندهٔ `HTMLGeolocationElement()` برای ایجاد یک نمونهٔ جدید از `HTMLGeolocationElement` استفاده کنند: تلاش برای انجام این کار منجر به خطای «illegal constructor» می‌شود.

### مثال‌ها

#### ایجاد یک نمونهٔ جدید از `HTMLGeolocationElement` به‌صورت برنامه‌نویسی‌شده

برای ایجاد برنامه‌نویسی‌شدهٔ یک نمونهٔ جدید از `HTMLGeolocationElement`، به‌جای تلاش برای استفادهٔ مستقیم از سازنده، یک نمونهٔ جدید از عنصر {{htmlelement("geolocation")}} را با استفاده از {{domxref("Document.createElement()")}} ایجاد می‌کنید:

```js
const geo = document.createElement("geolocation");
```

سپس می‌توانید با افزودن آن به DOM از آن استفاده کنید:

```js
document.body.append(geo);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- عنصر {{htmlelement("geolocation")}}
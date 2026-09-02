---
title: "MediaList: appendMedium() method"
short-title: appendMedium()
slug: Web/API/MediaList/appendMedium
page-type: web-api-instance-method
browser-compat: api.MediaList.appendMedium
---

{{APIRef("CSSOM")}}

متد `appendMedium()` از رابط {{DomxRef("MediaList")}} یک پرس‌وجوی رسانه (media query) را به لیست اضافه می‌کند. اگر پرس‌وجوی رسانه از قبل در مجموعه وجود داشته باشد، این متد کاری انجام نمی‌دهد.

## Syntax

```js-nolint
appendMedium(medium)
```

### پارامترها

- `medium`
  - : یک رشته (string) حاوی پرس‌وجوی رسانه‌ای که باید اضافه شود.

### مقدار بازگشتی

هیچ‌کدام ([undefined](/en-US/docs/Web/JavaScript/Reference/Global_Objects/undefined)).

## مثال‌ها

در مثال زیر، پرس‌وجوی رسانه `print` به `MediaList` مرتبط با اولین شیوه‌نامه (stylesheet) اعمال‌شده به سند جاری اضافه می‌شود.

```js
const stylesheet = document.styleSheets[0];
stylesheet.media.appendMedium("print");
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}
---
title: "MediaList: deleteMedium() method"
short-title: deleteMedium()
slug: Web/API/MediaList/deleteMedium
page-type: web-api-instance-method
browser-compat: api.MediaList.deleteMedium
---

{{APIRef("CSSOM")}}

متود `deleteMedium()` در رابط {{DOMxRef("MediaList")}}، پرس‌وجوی رسانه‌ای مشخص‌شده را از این `MediaList` حذف می‌کند.

## نحو (Syntax)

```js-nolint
deleteMedium(medium)
```

### پارامترها

- `medium`
  - : رشته‌ای حاوی پرس‌وجوی رسانه‌ای که باید از فهرست حذف شود.

### مقدار بازگشتی

هیچ (undefined).

### استثناها

- `NotFoundError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که پرس‌وجوی رسانه‌ای موردنظر برای حذف در فهرست وجود نداشته باشد.

## نمونه‌ها

مثال زیر، پرس‌وجوی رسانه‌ای `print` را از `MediaList` مرتبط با اولین استایل‌شیت اعمال‌شده بر سند جاری حذف می‌کند.

```js
const stylesheet = document.styleSheets[0];
stylesheet.media.deleteMedium("print");
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
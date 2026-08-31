---
title: "ContentIndexEvent: ContentIndexEvent() constructor"
short-title: ContentIndexEvent()
slug: Web/API/ContentIndexEvent/ContentIndexEvent
page-type: web-api-constructor
status:
  - experimental
browser-compat: api.ContentIndexEvent.ContentIndexEvent
---

{{APIRef("Content Index API")}}{{SeeCompatTable}}{{AvailableInWorkers("service")}}

سازندهٔ **`ContentIndexEvent()`** یک شیء جدید از نوع {{domxref("ContentIndexEvent")}} ایجاد می‌کند که نوع و سایر گزینه‌های آن مطابق پارامترهای داده‌شده تنظیم می‌شوند.

## نحو

```js-nolint
new ContentIndexEvent(type, options)
```

### پارامترها

- `type`
  - : رشته‌ای شامل نام رویداد. این مقدار به حروف بزرگ و کوچک حساس است (case-sensitive) و مرورگرها همیشه آن را روی `contentdelete` تنظیم می‌کنند.
- `options`
  - : یک شیء که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("ExtendableEvent/ExtendableEvent", "ExtendableEvent()")}}_، ویژگی‌های زیر را دارد:
    - `id`
      - : شناسه (`id`) محتوای فهرست‌شده‌ای که می‌خواهید شیء {{domxref("ContentIndex")}} آن را حذف کند.

### مقدار بازگشتی

یک شیء جدید از {{domxref("ContentIndexEvent")}} که با استفاده از گزینه‌های داده‌شده پیکربندی شده است.

## مثال‌ها

این مثال یک {{domxref('ContentIndexEvent')}} جدید با شناسهٔ مربوطه می‌سازد.

```js
const removeData = {
  id: "unique-content-id",
};

const ciEvent = new ContentIndexEvent("contentdelete", removeData);

ciEvent.id; // should return 'unique-content-id'
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- [مقالهٔ مقدماتی دربارهٔ Content Index API](https://developer.chrome.com/docs/capabilities/web-apis/content-indexing-api)
- [Service Worker API، به‌همراه اطلاعاتی دربارهٔ Cache و CacheStorage](/en-US/docs/Web/API/Service_Worker_API)
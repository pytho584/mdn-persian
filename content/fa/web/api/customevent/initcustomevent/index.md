---
title: "CustomEvent: initCustomEvent() method"
short-title: initCustomEvent()
slug: Web/API/CustomEvent/initCustomEvent
page-type: web-api-instance-method
status:
  - deprecated
browser-compat: api.CustomEvent.initCustomEvent
---

{{APIRef("DOM")}}{{Deprecated_header}}{{AvailableInWorkers}}

متد **`CustomEvent.initCustomEvent()`** یک شیء {{domxref("CustomEvent")}} را مقداردهی اولیه می‌کند.
اگر رویداد قبلاً ارسال شده باشد، این متد هیچ کاری انجام نمی‌دهد.

رویدادهایی که به این روش مقداردهی می‌شوند باید با متد {{domxref("Document.createEvent()")}} ساخته شده باشند.
این متد باید قبل از ارسال رویداد با استفاده از {{ domxref("EventTarget.dispatchEvent()") }} فراخوانی شود تا رویداد تنظیم گردد.
پس از ارسال، دیگر هیچ کاری انجام نمی‌دهد.

> [!NOTE]
> **دیگر از این متد استفاده نکنید، زیرا منسوخ شده است.**
>
> به‌جای استفاده از این قابلیت، از سازنده‌های اختصاصی رویداد مانند {{domxref("CustomEvent.CustomEvent", "CustomEvent()")}} استفاده کنید.
> بخش [ایجاد و ارسال رویدادها](/en-US/docs/Web/API/Document_Object_Model/Events#creating_and_dispatching_events) اطلاعات بیشتری درباره نحوه استفاده از آن‌ها ارائه می‌دهد.

## نحو (Syntax)

```js-nolint
initCustomEvent(type, canBubble, cancelable, detail)
```

### پارامترها

- `type`
  - : رشته‌ای شامل نام رویداد.
- `canBubble`
  - : یک مقدار بولین که نشان می‌دهد آیا رویداد در DOM به سمت بالا منتشر می‌شود یا نه.
- `cancelable`
  - : یک مقدار بولین که نشان می‌دهد آیا رویداد قابل لغو است یا نه.
- `detail`
  - : هر داده‌ای که از طریق ویژگی {{domxref("CustomEvent.detail")}} در اختیار handler قرار می‌گیرد.

### مقدار بازگشتی

هیچ (`undefined`).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("CustomEvent")}}
- سازنده‌ای که باید به‌جای این متد منسوخ استفاده شود: {{domxref("CustomEvent.CustomEvent", "CustomEvent()")}}.
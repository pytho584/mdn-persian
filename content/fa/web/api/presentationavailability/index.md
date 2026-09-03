---
title: "PresentationAvailability"
---

---
title: PresentationAvailability
slug: Web/API/PresentationAvailability
page-type: web-api-interface
status:
  - experimental
browser-compat: api.PresentationAvailability
---

{{SeeCompatTable}}{{securecontext_header}}{{APIRef("Presentation API")}}

یک شیء **`PresentationAvailability`** با [نمایشگرهای ارائه](https://www.w3.org/TR/presentation-api/#dfn-presentation-display) موجود مرتبط است و _در دسترس بودن نمایشگر ارائه_ را برای یک درخواست ارائه نشان می‌دهد. اگر [عامل کاربر کنترل‌کننده](https://www.w3.org/TR/presentation-api/#dfn-controlling-user-agent) بتواند در پس‌زمینه [فهرست نمایشگرهای ارائه موجود را پایش کند](https://www.w3.org/TR/presentation-api/#dfn-monitor-the-list-of-available-presentation-displays) (بدون درخواست معلق برای `start()`)، شیء `PresentationAvailability` _باید_ در یک [زمینه مرور کنترل‌کننده](https://www.w3.org/TR/presentation-api/#dfn-controlling-browsing-context) پیاده‌سازی شود.

ویژگی `value` _باید_ آخرین مقداری را که روی آن تنظیم شده است برگرداند. این مقدار توسط الگوریتم [پایش فهرست نمایشگرهای ارائه موجود](https://www.w3.org/TR/presentation-api/#dfn-monitor-the-list-of-available-presentation-displays) به‌روزرسانی می‌شود.

ویژگی `onchange` یک [مدیر رویداد](https://www.w3.org/TR/presentation-api/#dfn-event-handler) است که [نوع رویدادِ مدیر رویداد](https://www.w3.org/TR/presentation-api/#dfn-event-handler-event-type) متناظر با آن `change` است.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("PresentationAvailability.value")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک مقدار بولی که نشان می‌دهد آیا نمایشگر ارائه موردنظر در دسترس است یا خیر. ویژگی `value` _باید_ آخرین مقداری را که روی آن تنظیم شده است برگرداند.

### رویداد

- {{domxref("PresentationAvailability.change_event", "change")}} {{Experimental_Inline}}
  - : نشان می‌دهد که در دسترس بودن نمایشگر ارائه تغییر کرده است.

## متدهای نمونه

هیچ‌کدام.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}
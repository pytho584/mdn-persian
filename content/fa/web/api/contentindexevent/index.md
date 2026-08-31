---
title: "ContentIndexEvent"
---

---
title: ContentIndexEvent
slug: Web/API/ContentIndexEvent
page-type: web-api-interface
status:
  - experimental
browser-compat: api.ContentIndexEvent
---

{{APIRef("Content Index API")}}{{SeeCompatTable}}{{AvailableInWorkers("service")}}

اینترفیس **`ContentIndexEvent`** متعلق به [Content Index API](/en-US/docs/Web/API/Content_Index_API) است و شیءای را تعریف می‌کند که برای نمایش رویداد {{domxref("ServiceWorkerGlobalScope.contentdelete_event", 'contentdelete')}} استفاده می‌شود.

این رویداد به [حوزه سراسری](/en-US/docs/Web/API/ServiceWorkerGlobalScope) یک {{domxref('ServiceWorker')}} ارسال می‌شود و شامل شناسه (`id`) محتوای فهرست‌شده‌ای است که باید حذف شود.

رویداد {{domxref("ServiceWorkerGlobalScope.contentdelete_event", 'contentdelete')}} تنها زمانی فعال می‌شود که حذف در نتیجه تعامل با رابط کاربری داخلی مرورگر رخ دهد. این رویداد هنگام فراخوانی متد {{domxref('ContentIndex.delete')}} فعال نمی‌شود.

{{InheritanceDiagram}}

## سازنده

- {{domxref("ContentIndexEvent.ContentIndexEvent", "ContentIndexEvent()")}} {{Experimental_Inline}}
  - : یک شیء `ContentIndexEvent` جدید می‌سازد و برمی‌گرداند که نوع و سایر گزینه‌های آن مطابق مشخصات تنظیم شده‌اند.

## ویژگی‌های نمونه

_علاوه بر ویژگی‌های فهرست‌شده در زیر، این اینترفیس ویژگی‌های اینترفیس والد خود، {{domxref("ExtendableEvent")}} را به ارث می‌برد._

- {{domxref("ContentIndexEvent.id", "id")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک {{jsxref('String')}} که محتوای فهرست‌شده حذف‌شده را از طریق `id` آن شناسایی می‌کند.

## روش‌های نمونه

_در حالی که `ContentIndexEvent` هیچ روشی از خود ارائه نمی‌کند، تمام روش‌های مشخص‌شده توسط اینترفیس والد خود، {{domxref("ExtendableEvent")}} را به ارث می‌برد._

## مثال‌ها

این مثال اسکریپت [service worker](/en-US/docs/Web/API/ServiceWorker) را نشان می‌دهد که به رویداد {{domxref("ServiceWorkerGlobalScope.contentdelete_event", 'contentdelete')}} گوش می‌دهد و شناسه محتوای فهرست‌شده حذف‌شده را در کنسول ثبت می‌کند.

```js
self.addEventListener("contentdelete", (event) => {
  console.log(event.id);

  // logs content index id, which can then be used to determine what content to delete from your cache
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [مقاله مقدماتی درباره Content Index API](https://developer.chrome.com/docs/capabilities/web-apis/content-indexing-api)
- [Service Worker API، همراه با اطلاعاتی درباره Cache و CacheStorage](/en-US/docs/Web/API/Service_Worker_API)
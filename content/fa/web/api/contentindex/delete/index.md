---
title: "ContentIndex: delete() method"
short-title: delete()
slug: Web/API/ContentIndex/delete
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.ContentIndex.delete
---

{{APIRef("Content Index API")}}{{SeeCompatTable}}{{AvailableInWorkers}}

متد **`delete()`** در رابط {{domxref("ContentIndex")}} یک مورد را از فهرست محتوای فعلی خارج می‌کند (unregister).

> [!NOTE]
> فراخوانی `delete()` فقط بر فهرست تأثیر می‌گذارد. چیزی را از {{domxref('Cache')}} حذف نمی‌کند.

## Syntax

```js-nolint
delete(id)
```

### Parameters

- `id`
  - : شناسه‌ی یکتای محتوای فهرست‌شده‌ای که می‌خواهید شیء {{domxref("ContentIndex")}} آن را حذف کند.

### Return value

یک {{jsxref("Promise")}} برمی‌گرداند که با `undefined` resolve می‌شود.

### Exceptions

هیچ استثنایی پرتاب نمی‌شود.

## Examples

در زیر یک تابع ناهمگام (asynchronous) آمده است که یک مورد را از [فهرست محتوا](/en-US/docs/Web/API/Content_Index_API) حذف می‌کند. ما یک مرجع به {{domxref('ServiceWorkerRegistration')}} جاری دریافت می‌کنیم که به ما امکان دسترسی به ویژگی {{domxref('ServiceWorkerRegistration.index','index')}} و در نتیجه دسترسی به متد `delete` را می‌دهد.

```js
async function unregisterContent(article) {
  // reference registration
  const registration = await navigator.serviceWorker.ready;

  // feature detect Content Index
  if (!registration.index) return;

  // unregister content from index
  await registration.index.delete(article.id);
}
```

متد `delete` همچنین می‌تواند در محدوده‌ی [service worker](/en-US/docs/Web/API/ServiceWorker) استفاده شود.

```js
self.registration.index.delete("my-id");
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [مقاله‌ی مقدماتی درباره‌ی Content Index API](https://developer.chrome.com/docs/capabilities/web-apis/content-indexing-api)
- [Service Worker API، همراه با اطلاعاتی درباره‌ی Cache و CacheStorage](/en-US/docs/Web/API/Service_Worker_API)
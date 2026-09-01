---
title: "Document: hasUnpartitionedCookieAccess() method"
short-title: hasUnpartitionedCookieAccess()
slug: Web/API/Document/hasUnpartitionedCookieAccess
page-type: web-api-instance-method
browser-compat: api.Document.hasUnpartitionedCookieAccess
---

{{APIRef("Storage Access API")}}

متد **`hasUnpartitionedCookieAccess()`** از رابط {{domxref("Document")}} یک {{jsxref("Promise")}} برمی‌گرداند که با یک مقدار بولی resolve می‌شود و نشان می‌دهد آیا سند به کوکی‌های [شخص ثالث](/en-US/docs/Web/Privacy/Guides/Third-party_cookies) و [تقسیم‌نشده](/en-US/docs/Web/API/Storage_Access_API#unpartitioned_versus_partitioned_cookies) دسترسی دارد یا خیر.

این متد بخشی از [Storage Access API](/en-US/docs/Web/API/Storage_Access_API) است.

این متد نام جدیدی برای {{DOMxRef("Document.hasStorageAccess()")}} است.

## سینتکس

```js-nolint
hasUnpartitionedCookieAccess()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک مقدار بولی resolve می‌شود و نشان می‌دهد آیا سند به کوکی‌های شخص ثالث دسترسی دارد یا نه — اگر داشته باشد `true` و اگر نداشته باشد `false`.

برای جزئیات بیشتر به {{DOMxRef("Document.hasStorageAccess()")}} مراجعه کنید.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر {{domxref("Document")}} فعلی هنوز فعال نباشد، پرتاب می‌شود.

## مثال‌ها

```js
document.hasUnpartitionedCookieAccess().then((hasAccess) => {
  if (hasAccess) {
    // storage access has been granted already.
    console.log("cookie access granted");
  } else {
    // storage access hasn't been granted already;
    // you may want to call requestStorageAccess().
    console.log("cookie access denied");
  }
});
```

> [!NOTE]
> برای یک مثال کامل‌تر، به [استفاده از Storage Access API](/en-US/docs/Web/API/Storage_Access_API/Using) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("Document.hasStorageAccess()")}}, {{domxref("Document.requestStorageAccess()")}}, {{domxref("Document.requestStorageAccessFor()")}}
- [استفاده از Storage Access API](/en-US/docs/Web/API/Storage_Access_API/Using)
- [معرفی Storage Access API](https://webkit.org/blog/8124/introducing-storage-access-api/) (وبلاگ WebKit)
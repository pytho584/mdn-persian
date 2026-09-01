---
title: "Document: hasStorageAccess() method"
short-title: hasStorageAccess()
slug: Web/API/Document/hasStorageAccess
page-type: web-api-instance-method
browser-compat: api.Document.hasStorageAccess
---

{{APIRef("Storage Access API")}}

متد **`hasStorageAccess()`** از رابط {{domxref("Document")}} یک {{jsxref("Promise")}} برمی‌گرداند که با یک مقدار بولین (boolean) resolve می‌شود و نشان می‌دهد که آیا سند به [کوکی‌های شخص ثالث](/en-US/docs/Web/Privacy/Guides/Third-party_cookies) [تقسیم‌نشده (unpartitioned)](/en-US/docs/Web/API/Storage_Access_API#unpartitioned_versus_partitioned_cookies) دسترسی دارد یا نه.

این متد بخشی از [Storage Access API](/en-US/docs/Web/API/Storage_Access_API) است.

> [!NOTE]
> این متد نام دیگری برای {{DOMxRef("Document.hasUnpartitionedCookieAccess()")}} است. در حال حاضر برنامه‌ای برای حذف این متد به نفع {{DOMxRef("Document.hasUnpartitionedCookieAccess()")}} وجود ندارد.

## نحو

```js-nolint
hasStorageAccess()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک مقدار بولین resolve می‌شود و نشان می‌دهد که آیا سند به کوکی‌های شخص ثالث دسترسی دارد — اگر داشته باشد `true` و اگر نداشته باشد `false`.

نتیجه‌ای که این متد برمی‌گرداند ممکن است در چند شرایط نادقیق باشد:

1. ممکن است کاربر تنظیمات فعال مرورگری داشته باشد که کوکی‌های شخص ثالث را مسدود می‌کنند؛ در این حالت، ممکن است `true` برگردد حتی اگر کوکی‌های شخص ثالث همچنان در دسترس نباشند. برای مدیریت چنین وضعیتی، باید هر خطایی را که باعث می‌شود مقادیر کوکی قابل بازیابی نباشند به‌شکلی هوشمندانه مدیریت کنید؛ مثلاً به کاربر اطلاع دهید که دسترسی به تنظیمات شخصی‌سازی‌شده‌اش مسدود شده است و از او بخواهید برای استفاده از آن‌ها دوباره وارد سیستم شود.
2. ممکن است مرورگر به‌طور پیش‌فرض دسترسی به کوکی‌های شخص ثالث را مسدود نکند؛ در این حالت، ممکن است `false` برگردد حتی اگر کوکی‌های شخص ثالث قابل دسترسی باشند و نیازی به درخواست دسترسی ذخیره‌سازی نباشد (یعنی از طریق {{domxref("Document.requestStorageAccess()")}}). برای دور زدن این مشکل، می‌توانید {{domxref("Document.cookie")}} را بررسی کنید تا بفهمید آیا کوکی‌های شما قابل دسترسی هستند یا نه، و اگر نبودند، {{domxref("Document.requestStorageAccess()")}} را فراخوانی کنید.

> [!NOTE]
> اگر Promise resolve شود و هنگام فراخوانی اولیه تابع، یک رویداد ژست کاربر (user gesture) در حال پردازش باشد، هندلر resolve طوری اجرا می‌شود که گویی یک ژست کاربر در حال پردازش است؛ بنابراین می‌تواند APIهایی را فراخوانی کند که به فعال‌سازی کاربر نیاز دارند.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : در صورتی پرتاب می‌شود که {{domxref("Document")}} فعلی هنوز فعال نباشد.

## مثال‌ها

```js
document.hasStorageAccess().then((hasAccess) => {
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
> برای مثال کامل‌تر، [استفاده از Storage Access API](/en-US/docs/Web/API/Storage_Access_API/Using) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Document.hasUnpartitionedCookieAccess()")}}, {{domxref("Document.requestStorageAccess()")}}, {{domxref("Document.requestStorageAccessFor()")}}
- [استفاده از Storage Access API](/en-US/docs/Web/API/Storage_Access_API/Using)
- [معرفی Storage Access API](https://webkit.org/blog/8124/introducing-storage-access-api/) (وبلاگ WebKit)
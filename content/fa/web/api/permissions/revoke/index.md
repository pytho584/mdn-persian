---
title: "Permissions: revoke() method"
short-title: revoke()
slug: Web/API/Permissions/revoke
page-type: web-api-instance-method
status:
  - deprecated
browser-compat: api.Permissions.revoke
---

{{APIRef("Permissions API")}}{{AvailableInWorkers}}{{deprecated_header}}

متد **`revoke()`** از رابط {{domxref("Permissions")}} یک مجوزِ تنظیم‌شده را به حالت پیش‌فرض خود بازمی‌گرداند؛ حالتی که معمولاً `prompt` است. این متد روی شیء سراسری {{domxref("Permissions")}}، یعنی {{domxref("navigator.permissions")}}، فراخوانی می‌شود.

این متد از مشخصات اصلی Permissions API حذف شده است، زیرا کاربرد آن چندان واضح نیست. مدیریت مجوزها بر عهدهٔ مرورگر است و در مدل فعلی مجوزها، توسعه‌دهندهٔ سایت نمی‌تواند به‌صورت امری مجوزی را درخواست یا لغو کند. مرورگرها این API را پشت گزینه‌های آزمایشی (preferences) عرضه کرده‌اند، اما بعید است که در مسیر استانداردسازی قرار گیرد. برای زمینهٔ بیشتر، [بحث اصلیِ حذف `permissions.revoke()`](https://github.com/w3c/permissions/issues/46) را ببینید.

## سینتکس

```js-nolint
revoke(permissionDescriptor)
```

### پارامترها

- `permissionDescriptor`
  - : آبجکتی که گزینه‌های عملیات `revoke` را تنظیم می‌کند.
    گزینه‌های موجود برای این توصیفگر به نوع مجوز بستگی دارد.

    همهٔ مجوزها یک نام دارند:
    - `name`
      - : رشته‌ای شامل نام APIای که می‌خواهید مجوزهای آن را جستجو کنید.
        اگر نام مجوز توسط مرورگر پشتیبانی نشود، {{jsxref("Promise")}} برگشتی با یک {{jsxref("TypeError")}} رد خواهد شد.

    برای مجوزهای `push` همچنین می‌توانید موارد زیر را مشخص کنید:
    - `userVisibleOnly` {{optional_inline}}
      - : (فقط برای push؛ در Firefox پشتیبانی نمی‌شود — بخش «سازگاری مرورگر» را در پایین ببینید) مشخص می‌کند که آیا می‌خواهید برای هر پیام یک اعلان نمایش داده شود یا بتوانید اعلان‌های push بی‌صدا ارسال کنید.
        پیش‌فرض `false` است.

    برای مجوز `midi` همچنین می‌توانید موارد زیر را مشخص کنید:
    - `sysex` {{optional_inline}}
      - : مشخص می‌کند که آیا به پیام‌های system exclusive نیاز دارید و/یا آن‌ها را دریافت می‌کنید.
        پیش‌فرض `false` است.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که در صورت موفقیت با یک شیء {{domxref("PermissionStatus")}} resolve می‌شود؛ این شیء نتیجهٔ درخواست را نشان می‌دهد.

### استثناها

- {{jsxref("TypeError")}}
  - : بازیابی اطلاعات `PermissionDescriptor` به نحوی ناموفق بوده است، یا مجوز وجود ندارد یا در حال حاضر پشتیبانی نمی‌شود (مثلاً `midi`، یا `push` همراه با `userVisibleOnly`).

## مثال‌ها

این تابع می‌تواند توسط یک برنامه استفاده شود تا درخواست لغو مجوز مختص به Geolocation API خودش را بدهد.

```js
function revokePermission() {
  navigator.permissions.revoke({ name: "geolocation" }).then((result) => {
    report(result.state);
  });
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
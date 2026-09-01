---
title: "FormData: set() method"
short-title: set()
slug: Web/API/FormData/set
page-type: web-api-instance-method
browser-compat: api.FormData.set
---

{{APIRef("XMLHttpRequest API")}} {{AvailableInWorkers}}

متد **`set()`** در رابط {{domxref("FormData")}} مقدار جدیدی را برای یک کلید موجود در یک شیء `FormData` تنظیم می‌کند، یا اگر کلید از قبل وجود نداشته باشد، آن را به‌همراه مقدارش اضافه می‌کند.

تفاوت بین `set()` و {{domxref("FormData.append", "append()")}} این است که اگر کلید مشخص‌شده از قبل وجود داشته باشد، `set()` تمام مقادیر موجود را با مقدار جدید بازنویسی می‌کند، در حالی که `append()` مقدار جدید را به انتهای مجموعه مقادیر موجود اضافه می‌کند.

## نحو (Syntax)

```js-nolint
set(name, value)
set(name, value, filename)
```

### پارامترها

- `name`
  - : نام فیلدی که داده آن در `value` قرار دارد.
- `value`
  - : مقدار فیلد. این مقدار می‌تواند یک رشته یا {{domxref("Blob")}} باشد (شامل زیرکلاس‌هایی مانند {{domxref("File")}}). اگر هیچ‌کدام از این‌ها مشخص نشده باشند، مقدار به رشته تبدیل می‌شود.
- `filename` {{optional_inline}}
  - : نام فایلی که به سرور گزارش می‌شود (یک رشته)، زمانی که یک {{domxref("Blob")}} یا {{domxref("File")}} به‌عنوان پارامتر دوم ارسال می‌شود. نام پیش‌فرض برای اشیاء {{domxref("Blob")}}، «blob» است. نام پیش‌فرض برای اشیاء {{domxref("File")}}، نام خود فایل است.

> [!NOTE]
> اگر یک {{domxref("Blob")}} را به‌عنوان داده برای افزودن به شیء `FormData` مشخص کنید، نام فایلی که در هدر «Content-Disposition» به سرور گزارش می‌شود، در مرورگرهای مختلف متفاوت بود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

```js
formData.set("username", "Chris");
```

وقتی مقدار یک {{domxref("Blob")}} (یا یک {{domxref("File")}}) باشد، می‌توانید نام آن را با پارامتر `filename` مشخص کنید:

```js
formData.set("user-pic", myFileInput.files[0], "chris.jpg");
```

اگر مقدار یک رشته یا `Blob` نباشد، `set()` آن را به‌طور خودکار به رشته تبدیل می‌کند:

```js
formData.set("name", 72);
formData.get("name"); // "72"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از اشیاء FormData](/en-US/docs/Web/API/XMLHttpRequest_API/Using_FormData_Objects)
- {{HTMLElement("Form")}}
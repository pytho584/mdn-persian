---
title: "FormData: append() method"
---

---
title: "FormData: append() method"
short-title: append()
slug: Web/API/FormData/append
page-type: web-api-instance-method
browser-compat: api.FormData.append
---

{{APIRef("XMLHttpRequest API")}} {{AvailableInWorkers}}

متد **`append()`** از رابط {{domxref("FormData")}} یک مقدار جدید را به یک کلید موجود درون یک شیء `FormData` اضافه می‌کند، یا اگر کلید وجود نداشته باشد، آن را ایجاد می‌کند.

تفاوت بین {{domxref("FormData.set", "set()")}} و `append()` در این است که اگر کلید مشخص‌شده از قبل وجود داشته باشد، `set()` تمام مقادیر موجود را با مقدار جدید بازنویسی می‌کند، در حالی که `append()` مقدار جدید را به انتهای مجموعه مقادیر موجود اضافه می‌کند.

## نحو

```js-nolint
append(name, value)
append(name, value, filename)
```

### پارامترها

- `name`
  - : نام فیلدی که داده‌های آن در `value` قرار دارد.
- `value`
  - : مقدار فیلد. این می‌تواند یک رشته یا {{domxref("Blob")}} (شامل زیرکلاس‌هایی مانند {{domxref("File")}}) باشد. اگر هیچ‌کدام از این‌ها مشخص نشده باشند، مقدار به یک رشته تبدیل می‌شود.
- `filename` {{optional_inline}}
  - : نام فایلی که به سرور گزارش می‌شود (یک رشته)، زمانی که یک {{domxref("Blob")}} یا {{domxref("File")}} به عنوان پارامتر دوم ارسال می‌شود. نام پیش‌فرض برای اشیاء {{domxref("Blob")}} "blob" است. نام پیش‌فرض برای اشیاء {{domxref("File")}}، نام خود فایل است.

> [!NOTE]
> اگر یک {{domxref("Blob")}} را به عنوان داده‌ای که به شیء `FormData` اضافه می‌شود مشخص کنید، نام فایلی که در هدر "Content-Disposition" به سرور گزارش می‌شود، در مرورگرهای مختلف متفاوت بوده است.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مثال‌ها

```js
formData.append("username", "Chris");
```

زمانی که مقدار یک {{domxref("Blob")}} (یا یک {{domxref("File")}}) است، می‌توانید نام آن را با پارامتر `filename` مشخص کنید:

```js
formData.append("user-pic", myFileInput.files[0], "chris.jpg");
```

مانند داده‌های فرم معمولی، می‌توانید چندین مقدار با یک نام اضافه کنید:

```js
formData.append("user-pic", myFileInput.files[0], "chris1.jpg");
formData.append("user-pic", myFileInput.files[1], "chris2.jpg");
```

اگر مقدار یک رشته یا `Blob` نباشد، `append()` به طور خودکار آن را به رشته تبدیل می‌کند:

```js
formData.append("name", true);
formData.append("name", 72);
formData.getAll("name"); // ["true", "72"]
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از اشیاء FormData](/en-US/docs/Web/API/XMLHttpRequest_API/Using_FormData_Objects)
- {{HTMLElement("Form")}}
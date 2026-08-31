---
title: "ClipboardChangeEvent: changeId property"
---

---
title: "ClipboardChangeEvent: changeId property"
short-title: changeId
slug: Web/API/ClipboardChangeEvent/changeId
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.ClipboardChangeEvent.changeId
---

{{securecontext_header}}{{APIRef("Clipboard API")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`changeId`** از رابط {{domxref("ClipboardChangeEvent")}} یک عدد صحیح برمی‌گرداند که شناسه‌ی یکتا برای این عملیات خاص تغییر کلیپ‌بورد است.

این شناسه برای همان تغییر کلیپ‌بورد، در تمام پنجره‌ها و برگه‌هایی که کلید ذخیره‌سازی یکسانی دارند، یکسان است. این امر به برنامه‌ها امکان می‌دهد تا در مواقعی که چند پنجره اعلان یکسان تغییر کلیپ‌بورد را دریافت می‌کنند، رویدادهای تکراری را حذف کنند.

## مقدار

یک عدد صحیح. یک عدد صحیح ۱۲۸-بیتی که به‌صورت رمزنگاری‌شده مشتق می‌شود و پس از نوشتن چیزی در کلیپ‌بورد، تضمین می‌شود مقدار متفاوتی نسبت به مقدار پیش از عملیات نوشتن تولید کند.

## مثال‌ها

در این مثال، وقتی محتویات کلیپ‌بورد تغییر می‌کند، شنونده رویداد از ویژگی `ClipboardChangeEvent.changeId` استفاده می‌کند تا شناسه‌ی یکتای عملیات تغییر کلیپ‌بوردی که رویداد را فعال کرده است در کنسول ثبت کند.

```js
navigator.clipboard.addEventListener("clipboardchange", (event) => {
  console.log(event.changeId);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("ClipboardChangeEvent.types")}}
- {{domxref("ClipboardChangeEvent")}}
- {{domxref("ClipboardEvent")}}
- [Clipboard API](/en-US/docs/Web/API/Clipboard_API)
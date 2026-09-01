---
title: "FetchLaterResult"
slug: Web/API/FetchLaterResult
page-type: web-api-interface
status:
  - experimental
browser-compat: api.FetchLaterResult
---

{{APIRef("Fetch API")}}{{SeeCompatTable}}

رابط **`FetchLaterResult`** از [Fetch API](/en-US/docs/Web/API/Fetch_API) توسط متد {{domxref("Window.fetchLater()")}} پس از ایجاد یک درخواست به تعویق افتاده بازگردانده می‌شود.

این رابط شامل یک ویژگی به نام `activated` است که مشخص می‌کند آیا درخواست به تعویق افتاده ارسال شده است یا خیر.

پس از ارسال موفق، کل پاسخ - شامل بدنه و هدرها - نادیده گرفته می‌شود، بنابراین پاسخ درخواست به تعویق افتاده هرگز به رابط `FetchLaterResult` بازگردانده نمی‌شود.

## ویژگی‌های نمونه

- {{domxref('FetchLaterResult.activated')}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک فیلد بولی فقط خواندنی که مشخص می‌کند آیا درخواست به تعویق افتاده ارسال شده است. این مقدار ابتدا `false` است و سپس توسط مرورگر پس از ارسال درخواست به تعویق افتاده به‌روزرسانی می‌شود.

## مثال‌ها

### به تعویق انداختن یک درخواست `POST` برای حدود یک دقیقه و ایجاد یک تابع برای بررسی ارسال

```js
const result = fetchLater("https://report.example.com", {
  method: "POST",
  body: JSON.stringify(myReport),
  activateAfter: 60000 /* 1 minute */,
});

function checkIfFetched() {
  return result.activated;
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Fetch API](/en-US/docs/Web/API/Fetch_API)
- [Using Deferred Fetch](/en-US/docs/Web/API/Fetch_API/Using_Deferred_Fetch)
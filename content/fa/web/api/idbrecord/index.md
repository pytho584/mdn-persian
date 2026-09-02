---
title: IDBRecord
slug: Web/API/IDBRecord
page-type: web-api-interface
browser-compat: api.IDBRecord
---

{{APIRef("IndexedDB")}} {{AvailableInWorkers}}

رابط **`IDBRecord`** در [IndexedDB API](/en-US/docs/Web/API/IndexedDB_API) نمایانگر snapshot یک رکورد تکی در یک {{domxref("IDBObjectStore")}} یا {{domxref("IDBIndex")}} است.

درخواست دریافت رکوردها با استفاده از {{domxref("IDBObjectStore.getAllRecords()")}} یا {{domxref("IDBIndex.getAllRecords()")}} یک نمونه (instance) از {{domxref("IDBRequest")}} برمی‌گرداند. در صورت موفقیت، ویژگی {{domxref("IDBRequest.result", "result")}} شیء بازگشتی با آرایه‌ای از نمونه‌های `IDBRecord` پر می‌شود.

## ویژگی‌های نمونه

- `key` {{ReadOnlyInline}}
  - مقداری که کلید ثانویه رکورد را نشان می‌دهد. برای رکوردهای object store این مقدار با `primaryKey` یکسان است؛ برای رکوردهای index نیز این مقدار، کلید همان رکورد در داخل index است.
- `primaryKey` {{ReadOnlyInline}}
  - مقداری که کلید اصلی رکورد را نشان می‌دهد. از این کلید برای نمایش رکورد در {{domxref("IDBObjectStore")}} استفاده می‌شود.
- `value` {{ReadOnlyInline}}
  - مقداری که مقدار رکورد را نشان می‌دهد.

## متدهای نمونه

_هیچ‌کدام._

## مثال‌ها

### استفاده پایه

این مثال یک {{domxref("IDBObjectStore")}} را برای حداکثر ۱۰۰ رکورد که کلیدهایشان بعد از `"myKey"` قرار می‌گیرند جستجو می‌کند و نتایج را به ترتیب معکوس برمی‌گرداند.

کد ابتدا یک تراکنش روی {{domxref("IDBDatabase")}} به نام `db` ایجاد می‌کند (کد باز کردن پایگاه داده حذف شده است) و سپس از آن برای دریافت `IDBObjectStore` شامل فهرست مخاطبین استفاده می‌کند. سپس متد `getAllRecords()` را روی object store فراخوانی کرده و یک نمونه از {{domxref("IDBRequest")}} دریافت می‌کند. شنونده‌های رویداد برای رویدادهای `success` و `error` به این درخواست اضافه می‌شوند. در صورت موفقیت، نتیجه یعنی `event.target.result` در کنسول ثبت می‌شود (این مقدار همچنین از طریق `request.result` در دسترس است). این نتیجه شامل آرایه‌ای از نمونه‌های `IDBRecord` است. توجه کنید که چون این پرس‌وجو روی یک `IDBObjectStore` انجام شده است، مقدار `key` و `primaryKey` در هر رکورد یکسان است.

```js
// Create a transaction on the database and use it to get the contained store
const transaction = db.transaction(["contactsList"], "readonly");
const objectStore = transaction.objectStore("contactsList");

const query = IDBKeyRange.lowerBound("myKey", true);

const request = objectStore.getAllRecords({
  query,
  count: 100,
  direction: "prev",
});

request.addEventListener("success", (event) => {
  const myRecords = event.target.result; // Array of IDBRecord instances
  console.log(myRecords);
});

request.addEventListener("error", (event) => {
  console.error("Error retrieving records:", event.target.error);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("IDBObjectStore.getAllRecords()")}}
- {{domxref("IDBIndex.getAllRecords()")}}
- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال به‌صورت زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
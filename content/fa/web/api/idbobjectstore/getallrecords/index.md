---
title: "IDBObjectStore: getAllRecords() method"
short-title: getAllRecords()
slug: Web/API/IDBObjectStore/getAllRecords
page-type: web-api-instance-method
browser-compat: api.IDBObjectStore.getAllRecords
---

{{ APIRef("IndexedDB") }}

متد **`getAllRecords()`** از رابط {{domxref("IDBObjectStore")}} همهٔ رکوردها (شامل کلیدهای اصلی و مقادیر) را از object store بازیابی می‌کند.

`getAllRecords()` عملاً قابلیت‌های {{domxref("IDBObjectStore.getAllKeys", "getAllKeys()")}} و {{domxref("IDBObjectStore.getAll", "getAll()")}} را با شمارش همزمان کلیدهای اصلی و مقادیر ترکیب می‌کند. این عملیات ترکیبی باعث می‌شود برخی الگوهای بازیابی داده به‌طور قابل توجهی سریع‌تر از روش‌های جایگزین مانند پیمایش با cursorها باشند.

## سینتکس

```js-nolint
getAllRecords()
getAllRecords(options)
```

### پارامترها

یک شیء options که ویژگی‌های آن می‌تواند شامل موارد زیر باشد:

- `query` {{optional_inline}}
  - : یک کلید یا یک {{domxref("IDBKeyRange")}} که رکوردهای مورد نظر برای بازیابی را مشخص می‌کند. اگر این مقدار `null` باشد یا مشخص نشود، مرورگر از یک بازهٔ کلید بدون کران استفاده خواهد کرد.
- `count` {{optional_inline}}
  - : تعداد رکوردهایی که باید برگردانده شوند. اگر این مقدار از تعداد رکوردهای موجود در query بیشتر باشد، مرورگر فقط رکوردهای منطبق بر query را بازیابی می‌کند. اگر مقدار کمتر از `0` یا بیشتر از `2^32 - 1` باشد، یک استثنای {{jsxref("TypeError")}} پرتاب خواهد شد.
- `direction` {{optional_inline}}
  - : یک مقدار شمارشی که جهت پیمایش رکوردها را مشخص می‌کند و به تبع آن ترتیب بازگشت آن‌ها را تعیین می‌کند. مقادیر ممکن عبارتند از:
    - `next`
      - : رکوردها از ابتدا و به ترتیب صعودی کلید پیمایش می‌شوند. این مقدار پیش‌فرض است.
    - `nextunique`
      - : رکوردها از ابتدا و به ترتیب صعودی کلید پیمایش می‌شوند. از آنجا که کلیدهای تکراری در `IDBObjectStore`ها مجاز نیستند، این مقدار همان رکوردهای `next` را بازمی‌گرداند.
    - `prev`
      - : رکوردها از انتها و به ترتیب نزولی کلید پیمایش می‌شوند.
    - `prevunique`
      - : رکوردها از انتها و به ترتیب نزولی کلید پیمایش می‌شوند. از آنجا که کلیدهای تکراری در `IDBObjectStore`ها مجاز نیستند، این مقدار همان رکوردهای `prev` را بازمی‌گرداند.

### مقدار بازگشتی

یک شیء {{domxref("IDBRequest")}} که رویدادهای بعدی مرتبط با این عملیات روی آن ارسال می‌شوند.

اگر عملیات موفق باشد، مقدار ویژگی {{domxref("IDBRequest.result", "result")}} درخواست یک {{jsxref("Array", "آرایه")}} از نمونه‌های {{domxref("IDBRecord")}} است که همهٔ رکوردهای منطبق با query را، حداکثر تا تعداد مشخص‌شده توسط `count` (در صورت ارائه)، نشان می‌دهد.

هر نمونه {{domxref("IDBRecord")}} دارای ویژگی‌های زیر است:

- `key`
  - : مقداری نمایانگر کلید رکورد. این مقدار با ویژگی `primaryKey` یکسان است.
- `primaryKey`
  - : کلید اصلی رکورد.
- `value`
  - : مقداری نمایانگر مقدار رکورد.

### استثناها

این متد ممکن است یک {{domxref("DOMException")}} از انواع زیر صادر کند:

- `InvalidStateError` {{domxref("DOMException")}}
  - : در صورتی پرتاب می‌شود که {{domxref("IDBObjectStore")}} حذف یا برداشته شده باشد.
- `TransactionInactiveError` {{domxref("DOMException")}}
  - : در صورتی پرتاب می‌شود که تراکنش این {{domxref("IDBObjectStore")}} غیرفعال باشد.
- {{jsxref("TypeError")}} {{domxref("DOMException")}}
  - : در صورتی پرتاب می‌شود که پارامتر [`count`](#count) در بازهٔ بستهٔ `0` تا `2^32 - 1` نباشد.

## مثال‌ها

### استفادهٔ پایه

این مثال یک {{domxref("IDBObjectStore")}} را برای حداکثر ۱۰۰ رکورد که کلیدهایشان بعد از `"myKey"` قرار می‌گیرند، جستجو می‌کند و نتایج را به ترتیب معکوس مرتب می‌کند.

کد ابتدا یک تراکنش روی یک {{domxref("IDBDatabase")}} به نام `db` ایجاد می‌کند (کد باز کردن پایگاه داده حذف شده است) و سپس از آن برای دریافت یک `IDBObjectStore` حاوی فهرست مخاطبان استفاده می‌کند. سپس `getAllRecords()` را روی object store صدا می‌زند و یک نمونه {{domxref("IDBRequest")}} دریافت می‌کند. شنونده‌های رویداد برای رویدادهای `success` و `error` به این درخواست اضافه می‌شوند. در صورت موفقیت، نتیجهٔ `event.target.result` ثبت (log) می‌شود (این مقدار به‌عنوان `request.result` نیز در دسترس است). این نتیجه شامل آرایه‌ای از نمونه‌های `IDBRecord` است. توجه داشته باشید که چون این یک query روی یک `IDBObjectStore` است، `key` و `primaryKey` در هر رکورد مقدار یکسانی دارند.

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

- {{domxref("IDBObjectStore.getAll()")}}، {{domxref("IDBObjectStore.getAllKeys()")}}
- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم بازه‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و اعمال تغییرات در داده‌هایتان: {{domxref("IDBObjectStore")}}
- استفاده از cursorها: {{domxref("IDBCursor")}}
- [نمونهٔ خواندن سریع‌تر IndexedDB با getAllRecords()](https://microsoftedge.github.io/Demos/idb-getallrecords/) از مایکروسافت، ۲۰۲۵
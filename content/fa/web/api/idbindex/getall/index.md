---
title: "IDBIndex: getAll() method"
short-title: getAll()
slug: Web/API/IDBIndex/getAll
page-type: web-api-instance-method
browser-compat: api.IDBIndex.getAll
---

{{ APIRef("IndexedDB") }}

متد **`getAll()`** از رابط {{domxref("IDBIndex")}} همهٔ اشیاء داخل ایندکس را بازیابی می‌کند.

بررسی خاصیت `value` یک cursor هزینهٔ عملکردی به همراه دارد، زیرا شیء به‌صورت تنبل (lazy) ساخته می‌شود. برای استفاده از قابلیتی مانند `getAll()`، مرورگر باید همهٔ اشیاء را یک‌جا بسازد. اگر فقط به بررسی کلیدها علاقه‌مندید، برای نمونه، استفاده از یک [cursor](/en-US/docs/Web/API/IDBCursor) کارآمدتر است. اما اگر می‌خواهید آرایه‌ای از همهٔ اشیاء موجود در یک object store به‌دست آورید، باید از `getAll()` استفاده کنید.

## سینتکس

```js-nolint
getAll()
getAll(query)
getAll(query, count)
getAll(options)

```

### پارامترها

متد `getAll()` می‌تواند پارامترهای جداگانه یا یک شیء options واحد که این پارامترها را به‌صورت خاصیت در خود دارد دریافت کند.

پارامترها می‌توانند شامل این موارد باشند:

- `query` {{optional_inline}}
  - : یک کلید یا یک {{domxref("IDBKeyRange")}} که رکوردهای مورد نظر برای بازیابی را مشخص می‌کند. اگر این مقدار `null` باشد یا مشخص نشده باشد، مرورگر از یک بازهٔ کلید نامحدود استفاده خواهد کرد.
- `count` {{optional_inline}}
  - : تعداد رکوردهایی است که باید بازگردانده شوند. اگر این مقدار از تعداد رکوردهای موجود در query بیشتر باشد، مرورگر فقط رکوردهای منطبق با query را بازیابی می‌کند. اگر کمتر از `0` یا بیشتر از `2^32 - 1` باشد، یک استثنای {{jsxref("TypeError")}} پرتاب خواهد شد.

اگر یک پارامتر شیء مشخص شده باشد، خاصیت‌های آن می‌توانند شامل موارد زیر باشند:

- `query` {{optional_inline}}
  - : تعریف [`query`](#query) را در بخش بالا ببینید.
- `count` {{optional_inline}}
  - : تعریف [`count`](#count) را در بخش بالا ببینید.
- `direction` {{optional_inline}}
  - : یک مقدار شمارشی (enumerated) که جهت پیمایش اشیاء را مشخص می‌کند. مقادیر ممکن عبارت‌اند از:
    - `next`
      - : اشیاء از ابتدا، به ترتیب صعودی کلیدها پیمایش می‌شوند. این مقدار پیش‌فرض است.
    - `nextunique`
      - : اشیاء از ابتدا، به ترتیب صعودی کلیدها پیمایش می‌شوند. برای هر کلیدی که اشیاء تکراری دارد، فقط شیء نزدیک‌ترین به ابتدا بازگردانده می‌شود.
    - `prev`
      - : اشیاء از انتها، به ترتیب نزولی کلیدها پیمایش می‌شوند.
    - `prevunique`
      - : اشیاء از انتها، به ترتیب نزولی کلیدها پیمایش می‌شوند. برای هر کلیدی که اشیاء تکراری دارد، فقط شیء نزدیک‌ترین به ابتدا بازگردانده می‌شود.

### مقدار بازگشتی

یک شیء {{domxref("IDBRequest")}} که رویدادهای بعدی مرتبط با این عملیات روی آن صادر می‌شوند.

اگر عملیات موفقیت‌آمیز باشد، مقدار خاصیت {{domxref("IDBRequest.result", "result")}} درخواست، یک {{jsxref("Array")}} از مقادیر همهٔ رکوردهای منطبق با query داده‌شده است، تا حداکثر مقدار `count`، اگر `count` ارائه شده باشد.

### استثناها

این متد ممکن است یک {{domxref("DOMException")}} از انواع زیر را پرتاب کند:

- `TransactionInactiveError` {{domxref("DOMException")}}
  - : اگر تراکنشِ این {{domxref("IDBIndex")}} غیرفعال باشد پرتاب می‌شود.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر {{domxref("IDBIndex")}} حذف شده یا از بین رفته باشد پرتاب می‌شود.
- {{jsxref("TypeError")}} {{domxref("DOMException")}}
  - : اگر پارامتر [`count`](#count) بین `0` و `2^32 - 1` (شامل هر دو) نباشد پرتاب می‌شود.

## مثال‌ها

```js
const myIndex = objectStore.index("index");
const getAllRequest = myIndex.getAll();
getAllRequest.onsuccess = () => {
  console.log(getAllRequest.result);
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم بازه‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی داده‌ها و ایجاد تغییر در آن‌ها: {{domxref("IDBObjectStore")}}
- استفاده از cursorها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهدهٔ مثال به‌صورت زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
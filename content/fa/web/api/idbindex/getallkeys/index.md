---
title: "IDBIndex: getAllKeys() method"
---

---
title: "IDBIndex: getAllKeys() method"
short-title: getAllKeys()
slug: Web/API/IDBIndex/getAllKeys
page-type: web-api-instance-method
browser-compat: api.IDBIndex.getAllKeys
---

{{ APIRef("IndexedDB") }}

متد **`getAllKeys()`** از رابط {{domxref("IDBIndex")}} به‌صورت ناهمزمان کلیدهای اصلی همهٔ اشیاء داخل ایندکس را بازیابی می‌کند و آن‌ها را به‌عنوان `result` شیء درخواست قرار می‌دهد.

## سینتکس

```js-nolint
getAllKeys()
getAllKeys(query)
getAllKeys(query, count)
getAllKeys(options)
```

### پارامترها

متد `getAllKeys()` می‌تواند پارامترهای جداگانه یا یک شیء options واحد حاوی این پارامترها را به‌صورت ویژگی دریافت کند.

پارامترها می‌توانند شامل موارد زیر باشند:

- `query` {{optional_inline}}
  - : یک کلید یا یک {{domxref("IDBKeyRange")}} که کلیدهای مورد نظر برای بازیابی را مشخص می‌کند. اگر این مقدار `null` باشد یا مشخص نشده باشد، مرورگر از یک محدوده کلید نامحدود استفاده خواهد کرد.
- `count` {{optional_inline}}
  - : تعداد رکوردهایی که باید برگردانده شوند. اگر این مقدار از تعداد رکوردهای موجود در query بیشتر باشد، مرورگر فقط اولین مورد را بازیابی می‌کند. اگر کمتر از `0` یا بیشتر از `2^32 - 1` باشد، یک استثنای {{jsxref("TypeError")}} پرتاب خواهد شد.

اگر یک پارامتر شیء مشخص شده باشد، ویژگی‌های آن می‌توانند شامل موارد زیر باشند:

- `query` {{optional_inline}}
  - : تعریف [`query`](#query) قبلی را ببینید.
- `count` {{optional_inline}}
  - : تعریف [`count`](#count) قبلی را ببینید.
- `direction` {{optional_inline}}
  - : یک مقدار شمارشی که جهت پیمایش اشیاء را مشخص می‌کند. مقادیر ممکن عبارتند از:
    - `next`
      - : اشیاء از ابتدا و به ترتیب صعودی کلید پیمایش می‌شوند. این مقدار پیش‌فرض است.
    - `nextunique`
      - : اشیاء از ابتدا و به ترتیب صعودی کلید پیمایش می‌شوند. کلیدهایی که در چندین شیء تکرار شده‌اند فقط یک‌بار بازگردانده می‌شوند.
    - `prev`
      - : اشیاء از انتها و به ترتیب نزولی کلید پیمایش می‌شوند.
    - `prevunique`
      - : اشیاء از انتها و به ترتیب نزولی کلید پیمایش می‌شوند. کلیدهایی که در چندین شیء تکرار شده‌اند فقط یک‌بار بازگردانده می‌شوند.

### مقدار بازگشتی

یک شیء {{domxref("IDBRequest")}} که رویدادهای بعدی مربوط به این عملیات روی آن ارسال می‌شوند.

اگر عملیات موفقیت‌آمیز باشد، مقدار ویژگی {{domxref("IDBRequest.result", "result")}} درخواست، یک {{jsxref("Array")}} از کلیدهای همهٔ رکوردهای منطبق با query داده‌شده است، تا سقف مقدار `count`، اگر `count` ارائه شده باشد.

### استثناها

این متد ممکن است یک {{domxref("DOMException")}} از انواع زیر ایجاد کند:

- `TransactionInactiveError` {{domxref("DOMException")}}
  - : اگر تراکنش این {{domxref("IDBIndex")}} غیرفعال باشد پرتاب می‌شود.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر {{domxref("IDBIndex")}} حذف یا پاک شده باشد پرتاب می‌شود.
- {{jsxref("TypeError")}} {{domxref("DOMException")}}
  - : اگر پارامتر [`count`](#count) بین `0` و `2^32 - 1` (شامل هر دو) نباشد پرتاب می‌شود.

## مثال‌ها

```js
const myIndex = objectStore.index("index");
const getAllKeysRequest = myIndex.getAllKeys();
getAllKeysRequest.onsuccess = () => {
  console.log(getAllKeysRequest.result);
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
- تنظیم محدوده کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌ها: {{domxref("IDBObjectStore")}}
- استفاده از کرسرها: {{domxref("IDBCursor")}}
- مثال مرجع: [اعلان‌های کارها](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال به‌صورت زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
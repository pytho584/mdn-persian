---
title: "IDBObjectStore: getAll() method"
short-title: getAll()
slug: Web/API/IDBObjectStore/getAll
page-type: web-api-instance-method
browser-compat: api.IDBObjectStore.getAll
---

{{ APIRef("IndexedDB") }}

متد **`getAll()`** از رابط {{domxref("IDBObjectStore")}} یک شیء {{domxref("IDBRequest")}} برمی‌گرداند که شامل تمام اشیاء موجود در object store (ذخیره‌گاه شیء) است که با پارامتر مشخص شده مطابقت دارند، یا در صورت عدم ارائه پارامتر، تمام اشیاء موجود در ذخیره‌گاه را شامل می‌شود.

اگر مقداری با موفقیت یافت شود، یک کلون ساختاریافته (structured clone) از آن ایجاد شده و به عنوان نتیجه شیء درخواست تنظیم می‌شود.

این متد نتایج یکسانی برای موارد زیر تولید می‌کند:

- یک رکورد که در پایگاه داده وجود ندارد
- یک رکورد که مقدار undefined دارد

برای تشخیص این دو حالت از یکدیگر، می‌توانید:

1. متد {{domxref("IDBObjectStore.openCursor","openCursor()")}} را با همان کلید فراخوانی کنید. آن متد اگر رکورد وجود داشته باشد یک cursor (نشان‌گر) و اگر وجود نداشته باشد هیچ cursorای برمی‌گرداند.
2. متد {{domxref("IDBObjectStore.count","count()")}} را با همان کلید فراخوانی کنید که اگر ردیف وجود داشته باشد ۱ و اگر وجود نداشته باشد ۰ برمی‌گرداند.

## نحو (Syntax)

```js-nolint
getAll()
getAll(query)
getAll(query, count)
getAll(options)
```

### پارامترها

متد `getAll()` می‌تواند پارامترها را به صورت جداگانه یا به صورت یک شیء گزینه‌های واحد که شامل پارامترها به عنوان ویژگی‌ها است، دریافت کند.

پارامترها می‌توانند شامل موارد زیر باشند:

- `query` {{optional_inline}}
  - : یک کلید یا {{domxref("IDBKeyRange")}} (محدوده کلید) برای جستجو. اگر این مقدار مشخص نشود، به طور پیش‌فرض به یک محدوده کلیدی که تمام رکوردهای موجود در این object store را انتخاب می‌کند، تنظیم می‌شود.
- `count` {{optional_inline}}
  - : تعداد مقادیری را که در صورت یافتن بیش از یک مقدار باید برگردانده شوند، مشخص می‌کند. اگر کمتر از `0` یا بیشتر از `2^32 - 1` باشد، یک استثنای {{jsxref("TypeError")}} پرتاب می‌شود.

اگر یک پارامتر شیء مشخص شود، ویژگی‌های آن می‌توانند شامل موارد زیر باشند:

- `query` {{optional_inline}}
  - : به تعریف [`query`](#query) در بالا مراجعه کنید.
- `count` {{optional_inline}}
  - : به تعریف [`count`](#count) در بالا مراجعه کنید.
- `direction` {{optional_inline}}
  - : یک مقدار شمارشی که جهت پیمایش اشیاء را مشخص می‌کند. مقادیر ممکن عبارتند از:
    - `next`
      - : اشیاء از ابتدا، به ترتیب صعودی کلیدها پیمایش می‌شوند. این مقدار پیش‌فرض است.
    - `nextunique`
      - : اشیاء از ابتدا، به ترتیب صعودی کلیدها پیمایش می‌شوند. این مقدار همان اشیاء `next` را تولید می‌کند، زیرا کلیدهای تکراری در `IDBObjectStore`ها مجاز نیستند.
    - `prev`
      - : اشیاء از انتها، به ترتیب نزولی کلیدها پیمایش می‌شوند.
    - `prevunique`
      - : اشیاء از انتها، به ترتیب نزولی کلیدها پیمایش می‌شوند. این مقدار همان اشیاء `prev` را تولید می‌کند، زیرا کلیدهای تکراری در `IDBObjectStore`ها مجاز نیستند.

### مقدار بازگشتی

یک شیء {{domxref("IDBRequest")}} که رویدادهای بعدی مربوط به این عملیات روی آن شلیک می‌شوند.

اگر عملیات موفقیت‌آمیز باشد، مقدار ویژگی {{domxref("IDBRequest.result", "result")}} درخواست، یک {{jsxref("Array")}} از مقادیر تمام رکوردهای مطابق با query داده شده است، تا حداکثر مقدار `count`، در صورت ارائه `count`.

### استثناها (Exceptions)

این متد ممکن است یک {{domxref("DOMException")}} از یکی از انواع زیر را پرتاب کند:

- `TransactionInactiveError` {{domxref("DOMException")}}
  - : اگر تراکنش این {{domxref("IDBObjectStore")}} غیرفعال باشد، پرتاب می‌شود.
- `DataError` {{domxref("DOMException")}}
  - : اگر کلید یا محدوده کلید ارائه شده حاوی یک کلید نامعتبر یا null باشد، پرتاب می‌شود.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر {{domxref("IDBObjectStore")}} حذف یا پاک شده باشد، پرتاب می‌شود.
- {{jsxref("TypeError")}} {{domxref("DOMException")}}
  - : اگر پارامتر [`count`](#count) بین `0` و `2^32 - 1` (شامل هر دو) نباشد، پرتاب می‌شود.

## مشخصات (Specifications)

{{Specifications}}

## سازگاری با مرورگر (Browser compatibility)

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم محدوده‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌های خود: {{domxref("IDBObjectStore")}}
- استفاده از cursorها: {{domxref("IDBCursor")}}
- مثال مرجع: [اعلان‌های کارهای روزمره (To-do Notifications)](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
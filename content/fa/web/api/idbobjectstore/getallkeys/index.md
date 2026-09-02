---
title: "IDBObjectStore: getAllKeys() method"
short-title: getAllKeys()
slug: Web/API/IDBObjectStore/getAllKeys
page-type: web-api-instance-method
browser-compat: api.IDBObjectStore.getAllKeys
---

{{ APIRef("IndexedDB") }}

متد `getAllKeys()` از رابط {{domxref("IDBObjectStore")}} یک شیء {{domxref("IDBRequest")}} برمی‌گرداند که کلیدهای رکوردها را برای همه اشیاء موجود در object store (مخزن اشیاء) که با پارامتر مشخص‌شده مطابقت دارند، یا اگر پارامتری داده نشود، برای همه اشیاء موجود در store بازیابی می‌کند.

اگر مقداری با موفقیت یافت شود، یک structured clone از آن ایجاد شده و به عنوان نتیجه شیء درخواست تنظیم می‌شود.

این متد برای موارد زیر نتیجه یکسانی تولید می‌کند:

- رکوردی که در پایگاه داده وجود ندارد
- رکوردی که مقدار آن undefined است

برای تشخیص این دو حالت از یکدیگر، باید متد {{domxref("IDBObjectStore.openCursor","openCursor()")}} را با همان کلید فراخوانی کنید. این متد اگر رکورد وجود داشته باشد یک cursor ارائه می‌دهد و اگر وجود نداشته باشد هیچ cursorای ارائه نمی‌دهد.

## نحو

```js-nolint
getAllKeys()
getAllKeys(query)
getAllKeys(query, count)
getAllKeys(options)
```

### پارامترها

متد `getAllKeys()` می‌تواند پارامترهای جداگانه دریافت کند یا یک شیء options واحد که پارامترها را به عنوان ویژگی‌های خود دارد.

پارامترها می‌توانند شامل موارد زیر باشند:

- `query` {{optional_inline}}
  - : مقداری که یک {{domxref("IDBKeyRange")}} باشد یا به آن تبدیل شود. اگر این مقدار مشخص نشود، به‌طور پیش‌فرض یک محدوده کلید (key range) خواهد بود که همه رکوردهای این object store را انتخاب می‌کند.
- `count` {{optional_inline}}
  - : تعداد مقادیری را که در صورت یافتن بیش از یک مقدار باید برگردانده شوند، مشخص می‌کند. اگر کمتر از `0` یا بیشتر از `2^32 - 1` باشد، یک استثنای {{jsxref("TypeError")}} پرتاب خواهد شد.

اگر یک پارامتر شیء مشخص شده باشد، ویژگی‌های آن می‌توانند شامل موارد زیر باشند:

- `query` {{optional_inline}}
  - : تعریف [`query`](#query) را در بخش‌های پیشین ببینید.
- `count` {{optional_inline}}
  - : تعریف [`count`](#count) را در بخش‌های پیشین ببینید.
- `direction` {{optional_inline}}
  - : یک مقدار شمارشی (enumerated) که جهتی را مشخص می‌کند که اشیاء در آن پیمایش می‌شوند. مقادیر ممکن عبارتند از:
    - `next`
      - : اشیاء از ابتدا، به ترتیب کلید صعودی پیمایش می‌شوند. این مقدار پیش‌فرض است.
    - `nextunique`
      - : اشیاء از ابتدا، به ترتیب کلید صعودی پیمایش می‌شوند. این کار همان کلیدهای `next` را تولید می‌کند، زیرا کلیدهای تکراری در `IDBObjectStore`ها مجاز نیستند.
    - `prev`
      - : اشیاء از انتها، به ترتیب کلید نزولی پیمایش می‌شوند.
    - `prevunique`
      - : اشیاء از انتها، به ترتیب کلید نزولی پیمایش می‌شوند. این کار همان کلیدهای `prev` را تولید می‌کند، زیرا کلیدهای تکراری در `IDBObjectStore`ها مجاز نیستند.

### مقدار بازگشتی

یک شیء {{domxref("IDBRequest")}} که رویدادهای بعدی مرتبط با این عملیات روی آن فراخوانی می‌شوند.

اگر عملیات موفق باشد، مقدار ویژگی {{domxref("IDBRequest.result", "result")}} درخواست یک {{jsxref("Array")}} از کلیدهای همه رکوردهای منطبق با query داده‌شده است، تا حداکثر مقدار `count`، در صورتی که `count` ارائه شده باشد.

### استثناها

این متد ممکن است یک {{domxref("DOMException")}} از یکی از انواع زیر ایجاد کند:

- `TransactionInactiveError` {{domxref("DOMException")}}
  - : اگر تراکنش این {{domxref("IDBObjectStore")}} غیرفعال باشد، پرتاب می‌شود.
- `DataError` {{domxref("DOMException")}}
  - : اگر کلید یا محدوده کلید ارائه‌شده حاوی یک کلید نامعتبر باشد یا null باشد، پرتاب می‌شود.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر {{domxref("IDBObjectStore")}} حذف شده یا برداشته شده باشد، پرتاب می‌شود.
- {{jsxref("TypeError")}} {{domxref("DOMException")}}
  - : اگر پارامتر [`count`](#count) بین `0` و `2^32 - 1` (به‌صورت شامل) نباشد، پرتاب می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Using IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم محدوده کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌های خود: {{domxref("IDBObjectStore")}}
- استفاده از cursorها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([View the example live](https://mdn.github.io/dom-examples/to-do-notifications/)).
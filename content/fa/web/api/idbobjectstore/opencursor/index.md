---
title: "IDBObjectStore: openCursor() method"
short-title: openCursor()
slug: Web/API/IDBObjectStore/openCursor
page-type: web-api-instance-method
browser-compat: api.IDBObjectStore.openCursor
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

متد **`openCursor()`** از رابط {{domxref("IDBObjectStore")}} یک شیء {{domxref("IDBRequest")}} برمی‌گرداند و در یک رشتهٔ جداگانه، یک شیء جدید {{domxref("IDBCursorWithValue")}} بازمی‌گرداند. از این متد برای پیمایش رکوردهای یک object store با استفاده از cursor استفاده می‌شود.

## Syntax

```js-nolint
openCursor()
openCursor(query)
openCursor(query, direction)
```

### پارامترها

- `query` {{optional_inline}}
  - : یک کلید یا {{domxref("IDBKeyRange")}} برای جستجو. اگر یک کلید معتبرِ واحد ارسال شود، این پارامتر به‌طور پیش‌فرض به بازه‌ای تبدیل می‌شود که فقط همان کلید را شامل می‌شود. اگر چیزی ارسال نشود، به‌طور پیش‌فرض به بازه‌ای از کلیدها تبدیل می‌شود که همهٔ رکوردهای موجود در این object store را انتخاب می‌کند.
- `direction` {{optional_inline}}
  - : رشته‌ای که به cursor می‌گوید در چه جهتی حرکت کند. مقدار پیش‌فرض `next` است. مقادیر معتبر عبارت‌اند از:
    - `next`
      - : cursor در ابتدای store باز می‌شود؛ سپس همهٔ رکوردها، حتی موارد تکراری، را به ترتیب صعودی کلیدها بازمی‌گرداند.
    - `nextunique`
      - : cursor در ابتدای store باز می‌شود؛ سپس همهٔ رکوردهایی را که تکراری نیستند، به ترتیب صعودی کلیدها بازمی‌گرداند.
    - `prev`
      - : cursor در انتهای store باز می‌شود؛ سپس همهٔ رکوردها، حتی موارد تکراری، را به ترتیب نزولی کلیدها بازمی‌گرداند.
    - `prevunique`
      - : cursor در انتهای store باز می‌شود؛ سپس همهٔ رکوردهایی را که تکراری نیستند، به ترتیب نزولی کلیدها بازمی‌گرداند.

### مقدار بازگشتی

یک شیء {{domxref("IDBRequest")}} که رویدادهای بعدی مربوط به این عملیات روی آن رخ می‌دهند.

اگر عملیات موفق باشد، مقدار ویژگی {{domxref("IDBRequest.result", "result")}} درخواست به‌صورت زیر است:

- یک شیء {{domxref("IDBCursorWithValue")}} که به اولین رکورد منطبق با پرس‌وجوی داده‌شده اشاره می‌کند.
- اگر هیچ رکورد منطبقی یافت نشود، `null`.

### استثناها

این متد ممکن است یک {{domxref("DOMException")}} از انواع زیر ایجاد کند:

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر این {{domxref("IDBObjectStore")}} یا {{domxref("IDBIndex")}} حذف شده باشد، پرتاب می‌شود.
- `TransactionInactiveError` {{domxref("DOMException")}}
  - : اگر تراکنش این {{domxref("IDBObjectStore")}} غیرفعال باشد، پرتاب می‌شود.
- `DataError` {{domxref("DOMException")}}
  - : اگر کلید یا بازهٔ کلیدی مشخص‌شده نامعتبر باشد، پرتاب می‌شود.

## مثال‌ها

در این قطعهٔ ساده، یک تراکنش ایجاد می‌کنیم، یک object store را دریافت می‌کنیم و سپس با استفاده از cursor همهٔ رکوردهای موجود در object store را پیمایش می‌کنیم:

```js
const transaction = db.transaction("name", "readonly");
const objectStore = transaction.objectStore("name");
const request = objectStore.openCursor();
request.onsuccess = (event) => {
  const cursor = event.target.result;
  if (cursor) {
    // cursor.value contains the current record being iterated through
    // this is where you'd do something with the result
    cursor.continue();
  } else {
    // no more results
  }
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
- دریافت و ایجاد تغییرات در داده‌ها: {{domxref("IDBObjectStore")}}
- استفاده از cursorها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهدهٔ مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
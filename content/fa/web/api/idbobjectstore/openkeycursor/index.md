---
title: "IDBObjectStore: openKeyCursor() method"
short-title: openKeyCursor()
slug: Web/API/IDBObjectStore/openKeyCursor
page-type: web-api-instance-method
browser-compat: api.IDBObjectStore.openKeyCursor
---

{{ APIRef("IndexedDB") }}

متد **`openKeyCursor()`** از رابط {{domxref("IDBObjectStore")}} یک شیء {{domxref("IDBRequest")}} برمی‌گرداند که نتیجه آن یک {{domxref("IDBCursor")}} خواهد بود که می‌توان از آن برای پیمایش نتایج منطبق استفاده کرد. این متد برای پیمایش کلیدهای یک object store با استفاده از یک cursor به کار می‌رود.

برای تعیین اینکه آیا عملیات با موفقیت انجام شده است، به رویداد `success` نتیجه گوش دهید.

## نحو

```js-nolint
openKeyCursor()
openKeyCursor(query)
openKeyCursor(query, direction)
```

### پارامترها

- `query` {{optional_inline}}
  - : محدوده کلیدی که قرار است جستجو شود. اگر یک کلید معتبر واحد ارسال شود، به‌طور پیش‌فرض به محدوده‌ای شامل فقط همان کلید تبدیل می‌شود. اگر چیزی ارسال نشود، به‌طور پیش‌فرض به محدوده کلیدی می‌رسد که همه رکوردهای این object store را انتخاب می‌کند.
- `direction` {{optional_inline}}
  - : رشته‌ای که جهت حرکت cursor را مشخص می‌کند. مقدار پیش‌فرض `next` است. مقادیر معتبر عبارت‌اند از:
    - `next`
      - : cursor در ابتدای store باز می‌شود؛ سپس همه رکوردها، حتی موارد تکراری، به ترتیب صعودی کلیدها بازگردانده می‌شوند.
    - `nextunique`
      - : cursor در ابتدای store باز می‌شود؛ سپس همه رکوردهایی که تکراری نیستند به ترتیب صعودی کلیدها بازگردانده می‌شوند.
    - `prev`
      - : cursor در انتهای store باز می‌شود؛ سپس همه رکوردها، حتی موارد تکراری، به ترتیب نزولی کلیدها بازگردانده می‌شوند.
    - `prevunique`
      - : cursor در انتهای store باز می‌شود؛ سپس همه رکوردهایی که تکراری نیستند به ترتیب نزولی کلیدها بازگردانده می‌شوند.

### مقدار بازگشتی

یک شیء {{domxref("IDBRequest")}} که رویدادهای بعدی مربوط به این عملیات روی آن صادر می‌شوند.

اگر عملیات موفق باشد، مقدار خاصیت {{domxref("IDBRequest.result", "result")}} درخواست به صورت زیر است:

- یک شیء {{domxref("IDBCursor")}} که به اولین رکورد منطبق با query داده‌شده اشاره می‌کند.
- اگر هیچ رکورد منطبقی یافت نشود، مقدار `null`.

### استثناها

این متد ممکن است یک {{domxref("DOMException")}} از انواع زیر صادر کند:

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر این {{domxref("IDBObjectStore")}} یا {{domxref("IDBIndex")}} حذف شده باشد، صادر می‌شود.
- `TransactionInactiveError` {{domxref("DOMException")}}
  - : اگر تراکنش این {{domxref("IDBObjectStore")}} غیرفعال باشد، صادر می‌شود.
- `DataError` {{domxref("DOMException")}}
  - : اگر کلید یا محدوده کلید مشخص‌شده نامعتبر باشد، صادر می‌شود.

## مثال‌ها

در این قطعه ساده، یک تراکنش ایجاد می‌کنیم، یک object store را دریافت می‌کنیم و سپس از یک cursor برای پیمایش همه رکوردهای موجود در object store استفاده می‌کنیم:

```js
const transaction = db.transaction("name", "readonly");
const objectStore = transaction.objectStore("name");
const request = objectStore.openKeyCursor();
request.onsuccess = (event) => {
  const cursor = event.target.result;
  if (cursor) {
    // cursor.key contains the key of the current record being iterated through
    // note that there is no cursor.value, unlike for openCursor
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
- تنظیم محدوده کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌ها: {{domxref("IDBObjectStore")}}
- استفاده از cursorها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال به‌صورت زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
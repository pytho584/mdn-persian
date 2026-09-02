---
title: "IDBObjectStore: count() method"
---

---
title: "IDBObjectStore: count() method"
short-title: count()
slug: Web/API/IDBObjectStore/count
page-type: web-api-instance-method
browser-compat: api.IDBObjectStore.count
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

متد **`count()`** در رابط {{domxref("IDBObjectStore")}} یک شیء {{domxref("IDBRequest")}} بازمی‌گرداند و در یک نخ جداگانه، تعداد کل رکوردهایی را برمی‌گرداند که با کلید یا {{domxref("IDBKeyRange")}} ارائه‌شده مطابقت دارند. اگر هیچ آرگومانی ارسال نشود، تعداد کل رکوردهای فروشگاه را برمی‌گرداند.

## سینتکس

```js-nolint
count()
count(query)
```

### پارامترها

- `query` {{optional_inline}}
  - : یک کلید یا شیء {{domxref("IDBKeyRange")}} که محدوده‌ای از رکوردهایی را که می‌خواهید بشمارید مشخص می‌کند.

### مقدار بازگشتی

یک شیء {{domxref("IDBRequest")}} که رویدادهای بعدی مربوط به این عملیات روی آن صادر می‌شوند. اگر عملیات با موفقیت انجام شود، مقدار ویژگی {{domxref("IDBRequest.result", "result")}} درخواست، تعداد رکوردهایی است که با کوئری داده‌شده مطابقت دارند.

### استثناها

این متد ممکن است یک {{domxref("DOMException")}} از یکی از انواع زیر را صادر کند:

- `InvalidStateError` {{domxref("DOMException")}}
  - : هنگامی صادر می‌شود که این {{domxref("IDBObjectStore")}} حذف شده باشد.
- `TransactionInactiveError` {{domxref("DOMException")}}
  - : هنگامی صادر می‌شود که تراکنش این {{domxref("IDBObjectStore")}} غیرفعال باشد.
- `DataError` {{domxref("DOMException")}}
  - : هنگامی صادر می‌شود که کلید یا محدوده کلید مشخص‌شده نامعتبر باشد.

## مثال‌ها

در این قطعه ساده، یک تراکنش ایجاد می‌کنیم، یک فروشگاه شیء دریافت می‌کنیم و سپس با استفاده از `count()` تعداد رکوردهای فروشگاه را می‌شماریم — وقتی کنترل‌کننده موفقیت فعال می‌شود، مقدار شمارش (یک عدد صحیح) را در کنسول ثبت می‌کنیم.

```js
const transaction = db.transaction(["fThings"], "readonly");
const objectStore = transaction.objectStore("fThings");

const countRequest = objectStore.count();
countRequest.onsuccess = () => {
  console.log(countRequest.result);
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
- بازیابی و ایجاد تغییرات در داده‌های خود: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها: {{domxref("IDBCursor")}}
- مثال مرجع: [اعلان‌های کارها](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
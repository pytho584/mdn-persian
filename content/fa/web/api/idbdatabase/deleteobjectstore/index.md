---
title: "IDBDatabase: deleteObjectStore() method"
---

---
title: "IDBDatabase: deleteObjectStore() method"
short-title: deleteObjectStore()
slug: Web/API/IDBDatabase/deleteObjectStore
page-type: web-api-instance-method
browser-compat: api.IDBDatabase.deleteObjectStore
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

متد **`deleteObjectStore()`** از رابط {{domxref("IDBDatabase")}}، فروشگاه شیء (object store) با نام داده‌شده را در پایگاه‌داده متصل، همراه با هر نمایه (index) که به آن ارجاع می‌دهد، از بین می‌برد.

همانند {{ domxref("IDBDatabase.createObjectStore") }}، این متد را **فقط** در داخل یک تراکنش [`versionchange`](/en-US/docs/Web/API/IDBDatabase/versionchange_event) می‌توان فراخوانی کرد.

## نحو (Syntax)

```js-nolint
deleteObjectStore(name)
```

### پارامترها

- `name`
  - : نام فروشگاه شیئی که می‌خواهید حذف کنید. نام‌ها به بزرگی/کوچکی حروف حساس هستند.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر متد از یک callback تراکنش `versionchange` فراخوانی نشده باشد، پرتاب می‌شود.
- `TransactionInactiveError` {{domxref("DOMException")}}
  - : اگر درخواستی روی یک پایگاه‌داده مبدأ که وجود ندارد (مثلاً حذف یا پاک شده است) انجام شود، پرتاب می‌شود.
- `NotFoundError` {{domxref("DOMException")}}
  - : هنگام تلاش برای حذف یک فروشگاه شیء که وجود ندارد، پرتاب می‌شود.

## مثال‌ها

```js
const dbName = "sampleDB";
const dbVersion = 2;
const request = indexedDB.open(dbName, dbVersion);

request.onupgradeneeded = (event) => {
  const db = request.result;
  if (event.oldVersion < 1) {
    db.createObjectStore("store1");
  }

  if (event.oldVersion < 2) {
    db.deleteObjectStore("store1");
    db.createObjectStore("store2");
  }

  // etc. for version < 3, 4…
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
- تنظیم یک محدوده از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌های خود: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها (cursors): {{domxref("IDBCursor")}}
- مثال مرجع: [اعلان‌های کارهای روزانه](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
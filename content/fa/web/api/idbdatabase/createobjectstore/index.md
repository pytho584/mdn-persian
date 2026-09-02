---
title: "IDBDatabase: createObjectStore() method"
---

---
title: "IDBDatabase: createObjectStore() method"
short-title: createObjectStore()
slug: Web/API/IDBDatabase/createObjectStore
page-type: web-api-instance-method
browser-compat: api.IDBDatabase.createObjectStore
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

متد **`createObjectStore()`** از رابط {{domxref("IDBDatabase")}} یک {{domxref("IDBObjectStore")}} جدید ایجاد کرده و آن را بازمی‌گرداند.

این متد نام فروشگاه و همچنین یک شیء پارامتر دریافت می‌کند که به شما امکان می‌دهد ویژگی‌های اختیاری مهمی را تعریف کنید. می‌توانید از آن ویژگی برای شناسایی یکتای اشیاء منفرد در فروشگاه استفاده کنید. از آنجا که این ویژگی یک شناسه است، باید برای هر شیء یکتا باشد و هر شیء باید آن ویژگی را داشته باشد.

این متد _فقط_ در یک تراکنش [`versionchange`](/en-US/docs/Web/API/IDBDatabase/versionchange_event) قابل فراخوانی است.

## سینتکس

```js-nolint
createObjectStore(name)
createObjectStore(name, options)
```

### پارامترها

- `name`
  - : نام object store جدیدی که قرار است ایجاد شود. توجه داشته باشید که ایجاد object store با نام خالی نیز امکان‌پذیر است.
- `options` {{optional_inline}}
  - : یک شیء گزینه‌ها که ویژگی‌های آن پارامترهای اختیاری متد هستند. شامل ویژگی‌های زیر است:
    - `keyPath` {{optional_inline}}
      - : [مسیر کلید](/en-US/docs/Web/API/IndexedDB_API/Basic_Terminology#key_path) مورد استفاده برای object store جدید. اگر خالی یا مشخص نشده باشد، object store بدون مسیر کلید ایجاد می‌شود و از [کلیدهای خارج از خط](/en-US/docs/Web/API/IndexedDB_API/Basic_Terminology#out-of-line_key) استفاده می‌کند. همچنین می‌توانید یک آرایه را به عنوان `keyPath` ارسال کنید.
    - `autoIncrement` {{optional_inline}}
      - : اگر `true` باشد، object store دارای یک [مولد کلید](/en-US/docs/Web/API/IndexedDB_API/Basic_Terminology#key_generator) خواهد بود. پیش‌فرض آن `false` است.

### مقدار بازگشتی

یک {{domxref("IDBObjectStore")}} جدید.

### استثناها

این متد ممکن است یک {{domxref("DOMException")}} با `name` از یکی از انواع زیر ایجاد کند:

- `ConstraintError` {{domxref("DOMException")}}
  - : اگر object store ای با نام داده‌شده (بر اساس مقایسه حساس به بزرگی/کوچکی حروف) از قبل در پایگاه‌داده متصل وجود داشته باشد، پرتاب می‌شود.
- `InvalidAccessError` {{domxref("DOMException")}}
  - : اگر `autoIncrement` برابر `true` باشد و `keyPath` یک رشته خالی یا یک آرایه باشد، پرتاب می‌شود.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر متد از یک callback تراکنش `versionchange` فراخوانی نشده باشد، پرتاب می‌شود.
- `SyntaxError`
  - : اگر گزینه `keyPath` حاوی یک مسیر کلید نامعتبر باشد، پرتاب می‌شود.
- `TransactionInactiveError` {{domxref("DOMException")}}
  - : اگر درخواستی روی یک پایگاه‌داده مبدأ که وجود ندارد (مثلاً وقتی پایگاه‌داده حذف شده باشد) انجام شود، یا اگر تراکنش ارتقای مرتبط تکمیل شده باشد یا در حال پردازش یک درخواست باشد، پرتاب می‌شود.

## مثال‌ها

```js
// Let us open our database
const request = window.indexedDB.open("toDoList", 4);

// This handler is called when a new version of the database
// is created, either when one has not been created before
// or when a new version number is submitted by calling
// window.indexedDB.open().
// This handler is only supported in recent browsers.
request.onupgradeneeded = (event) => {
  const db = event.target.result;

  db.onerror = (event) => {
    note.appendChild(document.createElement("li")).textContent =
      "Error loading database.";
  };

  // Create an objectStore for this database

  const objectStore = db.createObjectStore("toDoList", {
    keyPath: "taskTitle",
  });

  // define what data items the objectStore will contain

  objectStore.createIndex("hours", "hours", { unique: false });
  objectStore.createIndex("minutes", "minutes", { unique: false });
  objectStore.createIndex("day", "day", { unique: false });
  objectStore.createIndex("month", "month", { unique: false });
  objectStore.createIndex("year", "year", { unique: false });

  objectStore.createIndex("notified", "notified", { unique: false });

  note.appendChild(document.createElement("li")).textContent =
    "Object store created.";
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
- تنظیم محدوده‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌های خود: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها: {{domxref("IDBCursor")}}
- مثال مرجع: [اعلان‌های کارهای روزانه](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
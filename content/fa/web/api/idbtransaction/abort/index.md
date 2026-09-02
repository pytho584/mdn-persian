---
title: "IDBTransaction: abort() method"
short-title: abort()
slug: Web/API/IDBTransaction/abort
page-type: web-api-instance-method
browser-compat: api.IDBTransaction.abort
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

متد **`abort()`** در رابط {{domxref("IDBTransaction")}} همهٔ تغییراتی را که روی اشیاء پایگاهداده مرتبط با این تراکنش انجام شده است، واگردانی (بازگردانی) میکند.

همهٔ اشیاء {{domxref("IDBRequest")}} در انتظار که در طول این تراکنش ایجاد شدهاند، ویژگی {{domxref("IDBRequest.error")}} آنها روی یک `AbortError` {{domxref("DOMException")}} تنظیم میشود.

## نحو (Syntax)

```js-nolint
abort()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر تراکنش قبلاً commit یا abort شده باشد، پرتاب میشود.

## مثال‌ها

در قطعه‌کد زیر، یک تراکنش خواندن/نوشتن روی پایگاه‌داده باز می‌کنیم و چند داده به object store اضافه می‌کنیم. همچنین به توابع متصل به رویداد‌های تراکنش توجه کنید که نتیجهٔ باز شدن تراکنش را در صورت موفقیت یا شکست گزارش می‌دهند. در پایان، هر فعالیتی را که در تراکنش جاری انجام شده است با استفاده از `abort()` لغو می‌کنیم. برای یک مثال کامل و قابل اجرا، برنامهٔ [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ما را ببینید ([مشاهدهٔ مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).

```js
const note = document.getElementById("notifications");

// an instance of a db object for us to store the IDB data in
let db;

// Let us open our database
const DBOpenRequest = window.indexedDB.open("toDoList", 4);

DBOpenRequest.onsuccess = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Database initialized.";

  // store the result of opening the database in the db variable. This is used a lot below
  db = DBOpenRequest.result;

  // Run the addData() function to add the data to the database
  addData();
};

function addData() {
  // Create a new object ready for being inserted into the IDB
  const newItem = [
    {
      taskTitle: "Walk dog",
      hours: 19,
      minutes: 30,
      day: 24,
      month: "December",
      year: 2013,
      notified: "no",
    },
  ];

  // open a read/write db transaction, ready for adding the data
  const transaction = db.transaction(["toDoList"], "readwrite");

  // report on the success of opening the transaction
  transaction.oncomplete = (event) => {
    note.appendChild(document.createElement("li")).textContent =
      "Transaction completed: database modification finished.";
  };

  transaction.onerror = (event) => {
    note.appendChild(document.createElement("li")).textContent =
      "Transaction not opened due to error. Duplicate items not allowed.";
  };

  // create an object store on the transaction
  const objectStore = transaction.objectStore("toDoList");

  // add our newItem object to the object store
  const objectStoreRequest = objectStore.add(newItem[0]);

  objectStoreRequest.onsuccess = (event) => {
    // report the success of the request (this does not mean the item
    // has been stored successfully in the DB - for that you need transaction.onsuccess)
    note.appendChild(document.createElement("li")).textContent =
      "Request successful.";
  };

  // Abort the transaction we just did
  transaction.abort();
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم محدودهٔ کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌ها: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها (cursors): {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهدهٔ مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
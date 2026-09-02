---
title: "IDBTransaction: db property"
short-title: db
slug: Web/API/IDBTransaction/db
page-type: web-api-instance-property
browser-compat: api.IDBTransaction.db
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

خاصیت خواندنی **`db`** از رابط {{domxref("IDBTransaction")}}، اتصال پایگاه‌داده‌ای که این تراکنش با آن مرتبط است را برمی‌گرداند.

## مقدار

یک شیء {{domxref("IDBDatabase")}}.

## مثال‌ها

در قطعه کد زیر، یک تراکنش خواندن/نوشتن روی پایگاه‌داده خود باز می‌کنیم و داده‌هایی را به یک object store اضافه می‌کنیم. همچنین به توابع متصل به handlerهای رویداد تراکنش توجه کنید که نتیجه باز شدن تراکنش را در صورت موفقیت یا شکست گزارش می‌دهند. در پایان، اتصال پایگاه‌داده مرتبط را با استفاده از `db` برمی‌گردانیم. برای یک مثال کامل کاری، به برنامه [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) مراجعه کنید ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).

```js
const note = document.getElementById("notifications");

// an instance of a db object for us to store the IDB data in
let db;

// Let us open our database
const DBOpenRequest = window.indexedDB.open("toDoList", 4);

DBOpenRequest.onsuccess = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Database initialized.";

  // store the result of opening the database in the db variable.
  // This is used a lot below
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

  // Return the database (IDBDatabase) connection with which this transaction is associated
  transaction.db;
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
- تنظیم محدوده‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و اعمال تغییرات در داده‌هایتان: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
```
---
title: "IDBObjectStore: keyPath property"
short-title: keyPath
slug: Web/API/IDBObjectStore/keyPath
page-type: web-api-instance-property
browser-compat: api.IDBObjectStore.keyPath
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`keyPath`** از رابط {{domxref("IDBObjectStore")}}، [مسیر کلید](/en-US/docs/Web/API/IndexedDB_API/Basic_Terminology#key_path) این مخزن شیء را برمی‌گرداند.

اگر مقدار این ویژگی `null` باشد، برنامه باید برای هر عملیات تغییر، یک کلید فراهم کند.

## مقدار

این ویژگی می‌تواند مقداری از هر نوعی داشته باشد.

## مثال‌ها

در قطعه‌کد زیر، یک تراکنش خواندن/نوشتن روی پایگاه‌داده باز می‌کنیم و داده‌هایی را با استفاده از `add()` به یک مخزن شیء اضافه می‌کنیم. پس از ساخته‌شدن مخزن شیء، مقدار `objectStore.keyPath` را در کنسول چاپ می‌کنیم. برای مشاهدهٔ یک مثال کامل و قابل اجرا، برنامهٔ [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) را ببینید ([مشاهدهٔ مثال به‌صورت زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).

```js
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
  // Create a new object ready to insert into the IDB
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

  // report on the success of the transaction completing, when everything is done
  transaction.oncomplete = (event) => {
    note.appendChild(document.createElement("li")).textContent =
      "Transaction completed.";
  };

  transaction.onerror = (event) => {
    note.appendChild(document.createElement("li")).textContent =
      "Transaction not opened due to error. Duplicate items not allowed.";
  };

  // create an object store on the transaction
  const objectStore = transaction.objectStore("toDoList");
  console.log(objectStore.keyPath);

  // Make a request to add our newItem object to the object store
  const objectStoreRequest = objectStore.add(newItem[0]);

  objectStoreRequest.onsuccess = (event) => {
    // report the success of our request
    note.appendChild(document.createElement("li")).textContent =
      "Request successful.";
  };
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
- تنظیم بازه‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی داده‌ها و ایجاد تغییر در آن‌ها: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهدهٔ مثال به‌صورت زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
```
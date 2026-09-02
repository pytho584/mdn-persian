---
title: "IDBObjectStore: name property"
short-title: name
slug: Web/API/IDBObjectStore/name
page-type: web-api-instance-property
browser-compat: api.IDBObjectStore.name
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

خاصیت **`name`** از رابط {{domxref("IDBObjectStore")}} نشان‌دهنده نام این object store است.

## مقدار

یک رشته که شامل نام object store است.

### استثناها

چندین استثنا ممکن است هنگام تلاش برای تغییر نام object store رخ دهد.

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر object store حذف شده باشد یا تراکنش جاری یک تراکنش ارتقاء (upgrade) نباشد، پرتاب می‌شود. شما فقط می‌توانید در حین تراکنش‌های ارتقاء (یعنی وقتی حالت `versionchange` است) نام ایندکس‌ها را تغییر دهید.
- `TransactionInactiveError` {{domxref("DOMException")}}
  - : اگر تراکنش جاری فعال نباشد، پرتاب می‌شود.
- `ConstraintError` {{domxref("DOMException")}}
  - : اگر یک object store از قبل از `name` مشخص شده استفاده کند، پرتاب می‌شود.

## مثال‌ها

در قطعه کد زیر، ما یک تراکنش خواندن/نوشتن روی پایگاه داده باز می‌کنیم و با استفاده از `add()` داده‌هایی را به یک object store اضافه می‌کنیم. پس از ایجاد object store، مقدار `objectStore.name` را در کنسول ثبت می‌کنیم. برای یک مثال کامل کار، برنامه [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ما را ببینید ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).

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
  console.log(objectStore.name);

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
- تنظیم یک محدوده از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌های خود: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
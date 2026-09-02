---
title: "IDBObjectStore: indexNames property"
short-title: indexNames
slug: Web/API/IDBObjectStore/indexNames
page-type: web-api-instance-property
browser-compat: api.IDBObjectStore.indexNames
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`indexNames`** در رابط {{domxref("IDBObjectStore")}} فهرستی از نام [indexes](/en-US/docs/Web/API/IndexedDB_API/Basic_Terminology#index) روی اشیاء موجود در این object store را برمی‌گرداند.

## Value

یک {{domxref("DOMStringList")}}.

## Examples

در قطعه کد زیر، یک تراکنش خواندن/نوشتن روی پایگاه داده باز می‌کنیم و با استفاده از `add()` داده‌هایی را به یک object store اضافه می‌کنیم. پس از اینکه object store ایجاد شد، مقدار `objectStore.indexNames` را در کنسول ثبت می‌کنیم. برای مشاهده مثال کامل، برنامه [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) را ببینید ([view example live](https://mdn.github.io/dom-examples/to-do-notifications/)).

```js
// Let us open our database
const DBOpenRequest = window.indexedDB.open("toDoList", 4);

DBOpenRequest.onsuccess = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Database initialized.";

  // store the result of opening the database in the db variable.
  // This is used a lot below
  db = this.result;

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
  console.log(objectStore.indexNames);

  // Make a request to add our newItem object to the object store
  const objectStoreRequest = objectStore.add(newItem[0]);

  objectStoreRequest.onsuccess = (event) => {
    // report the success of our request
    note.appendChild(document.createElement("li")).textContent =
      "Request successful.";
  };
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Using IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم محدوده‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌ها: {{domxref("IDBObjectStore")}}
- استفاده از cursorها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([View the example live](https://mdn.github.io/dom-examples/to-do-notifications/))
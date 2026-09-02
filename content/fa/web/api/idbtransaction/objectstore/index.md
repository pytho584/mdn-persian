---
title: "IDBTransaction: objectStore() method"
---

---
title: "IDBTransaction: objectStore() method"
short-title: objectStore()
slug: Web/API/IDBTransaction/objectStore
page-type: web-api-instance-method
browser-compat: api.IDBTransaction.objectStore
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

متد **`objectStore()`** از رابط {{domxref("IDBTransaction")}} یک فروشگاه شیء (object store) را برمی‌گرداند که قبلاً به محدودهٔ این تراکنش اضافه شده است.

هر بار که این متد بر روی همان شیء تراکنش و با همان نام فراخوانی شود، همان نمونهٔ {{domxref("IDBObjectStore")}} را برمی‌گرداند. اگر این متد بر روی یک شیء تراکنش متفاوت فراخوانی شود، نمونهٔ متفاوتی از {{domxref("IDBObjectStore")}} برگردانده می‌شود.

## سینتکس

```js-nolint
objectStore(name)
```

### پارامترها

- `name`
  - : نام فروشگاه شیء درخواستی.

### مقدار بازگشتی

یک شیء {{domxref("IDBObjectStore")}} برای دسترسی به فروشگاه شیء.

### استثناها

- `NotFoundError` {{domxref("DOMException")}}
  - : اگر فروشگاه شیء درخواستی در محدودهٔ این تراکنش نباشد، پرتاب می‌شود.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر درخواست بر روی یک شیء منبع که حذف یا پاک شده است انجام شود، یا اگر تراکنش به پایان رسیده باشد، پرتاب می‌شود.

## مثال‌ها

در قطعه‌کد زیر، یک تراکنش خواندن/نوشتن روی پایگاه‌دادهٔ خود باز می‌کنیم و داده‌هایی را به یک فروشگاه شیء اضافه می‌کنیم. همچنین به توابع متصل‌شده به رویدادگردان‌های تراکنش توجه کنید که نتیجهٔ باز شدن تراکنش را در صورت موفقیت یا شکست گزارش می‌دهند. برای مشاهدهٔ یک مثال کامل و قابل اجرا، به برنامهٔ [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) مراجعه کنید ([مشاهدهٔ مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).

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
- بازیابی و ایجاد تغییرات در داده‌ها: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها (cursors): {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهدهٔ مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
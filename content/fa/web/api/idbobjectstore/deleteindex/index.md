---
title: "IDBObjectStore: deleteIndex() method"
short-title: deleteIndex()
slug: Web/API/IDBObjectStore/deleteIndex
page-type: web-api-instance-method
browser-compat: api.IDBObjectStore.deleteIndex
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

متد **`deleteIndex()`** از رابط {{domxref("IDBObjectStore")}} ایندکس با نام مشخص‌شده را در پایگاه‌داده متصل حذف می‌کند و در هنگام ارتقای نسخه استفاده می‌شود.

توجه داشته باشید که این متد فقط باید از یک callback در حالت تراکنش `VersionChange` فراخوانی شود. همچنین این متد به‌صورت هم‌زمان ویژگی {{domxref("IDBObjectStore.indexNames")}} را تغییر می‌دهد.

## Syntax

```js-nolint
deleteIndex(indexName)
```

### Parameters

- `indexName`
  - : نام ایندکس موجود که باید حذف شود.

### Return value

هیچ ({{jsxref("undefined")}}).

### Exceptions

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر متد از یک callback در حالت تراکنش `versionchange` فراخوانی نشده باشد، پرتاب می‌شود.
- `TransactionInactiveError` {{domxref("DOMException")}}
  - : اگر تراکنشی که این {{domxref("IDBObjectStore")}} به آن تعلق دارد فعال نباشد (مثلاً حذف شده یا از بین رفته باشد)، پرتاب می‌شود.
- `NotFoundError` {{domxref("DOMException")}}
  - : اگر ایندکسی با نام داده‌شده (با حساسیت به حروف بزرگ و کوچک) در پایگاه‌داده وجود نداشته باشد، پرتاب می‌شود.

## Examples

در مثال زیر، می‌توانید استفاده از handler رویداد {{domxref("IDBOpenDBRequest.upgradeneeded_event", "onupgradeneeded")}} را برای به‌روزرسانی ساختار پایگاه‌داده در صورت بارگذاری نسخه‌ای با شماره بالاتر ببینید. از {{domxref("IDBObjectStore.createIndex")}} برای ایجاد ایندکس‌های جدید روی object store استفاده می‌شود و پس از آن، ایندکس‌های قدیمی غیرضروری را با `deleteIndex()` حذف می‌کنیم. برای یک مثال کامل و قابل اجرا، برنامه [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) را ببینید ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).

```js
let db;

// Let us open our database
const DBOpenRequest = window.indexedDB.open("toDoList", 4);

// these two event handlers act on the database being opened successfully, or not
DBOpenRequest.onerror = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Error loading database.";
};

DBOpenRequest.onsuccess = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Database initialized.";

  // store the result of opening the database in the db variable. This is used a lot below
  db = event.target.result;

  // Run the displayData() function to populate the task list with all the to-do list data already in the IDB
  displayData();
};

// This event handles the event whereby a new version of the database needs to be created
// Either one has not been created before, or a new version number has been submitted via the
// window.indexedDB.open line above
// it is only implemented in recent browsers
DBOpenRequest.onupgradeneeded = (event) => {
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

  objectStore.deleteIndex("seconds");
  objectStore.deleteIndex("contact");
};
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم محدوده‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌ها: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها (cursors): {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
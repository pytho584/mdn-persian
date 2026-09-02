---
title: "IDBRequest: transaction property"
short-title: transaction
slug: Web/API/IDBRequest/transaction
page-type: web-api-instance-property
browser-compat: api.IDBRequest.transaction
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`transaction`** در رابط `IDBRequest`، تراکنشِ مربوط به درخواست را برمی‌گرداند؛ یعنی تراکنشی که درخواست در داخلِ آن انجام می‌شود.

این ویژگی می‌تواند برای درخواست‌هایی که درونِ تراکنش‌ها انجام نشده‌اند، `null` باشد؛ مانند درخواست‌هایی که از {{domxref("IDBFactory.open")}} بازگردانده می‌شوند. در این حالت فقط در حال اتصال به یک پایگاه‌داده هستید، بنابراین تراکنشی برای بازگرداندن وجود ندارد. اگر هنگام باز کردن یک پایگاه‌داده به ارتقای نسخه نیاز باشد، در طولِ مدیریت‌کنندهٔ رویدادِ {{domxref("IDBOpenDBRequest.upgradeneeded_event", "upgradeneeded")}}، ویژگی **`transaction`** یک {{domxref("IDBTransaction")}} با {{domxref("IDBTransaction.mode", "mode")}} برابر با `"versionchange"` خواهد بود و می‌توان از آن برای دسترسی به object storeها و ایندکس‌های موجود یا لغوِ ارتقا استفاده کرد. پس از ارتقا، ویژگی **`transaction`** دوباره `null` خواهد بود.

## مقدار

یک {{domxref("IDBTransaction")}}.

## مثال‌ها

مثال زیر عنوانِ یک رکورد مشخص را درخواست می‌کند؛ در `onsuccess` رکورد مرتبط از {{domxref("IDBObjectStore")}} گرفته می‌شود (به‌صورت `objectStoreTitleRequest.result` در دسترس است)، یکی از ویژگی‌های رکورد به‌روزرسانی می‌شود و سپس رکورد به‌روزرسانی‌شده در درخواستی دیگر به object store بازگردانده می‌شود. منشأ درخواست‌ها در کنسول توسعه‌دهنده ثبت می‌شود — هر دو از یک تراکنش سرچشمه می‌گیرند. برای یک مثال کامل و قابل اجرا، برنامهٔ [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) را ببینید ([مشاهدهٔ مثال به‌صورت زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).

```js
const title = "Walk dog";

// Open up a transaction as usual
const objectStore = db
  .transaction(["toDoList"], "readwrite")
  .objectStore("toDoList");

// Get the to-do list object that has this title as its title
const objectStoreTitleRequest = objectStore.get(title);

objectStoreTitleRequest.onsuccess = () => {
  // Grab the data object returned as the result
  const data = objectStoreTitleRequest.result;

  // Update the notified value in the object to "yes"
  data.notified = "yes";

  // Create another request that inserts the item back
  // into the database
  const updateTitleRequest = objectStore.put(data);

  // Log the transaction that originated this request
  console.log(
    `The transaction that originated this request is ${updateTitleRequest.transaction}`,
  );

  // When this new request succeeds, run the displayData()
  // function again to update the display
  updateTitleRequest.onsuccess = () => {
    displayData();
  };
};
```

این مثال نشان می‌دهد که چگونه می‌توان از ویژگی **`transaction`** در طولِ ارتقای نسخه برای دسترسی به object storeهای موجود استفاده کرد:

```js
const openRequest = indexedDB.open("db", 2);
console.log(openRequest.transaction); // Will log "null".

openRequest.onupgradeneeded = (event) => {
  console.log(openRequest.transaction.mode); // Will log "versionchange".
  const db = openRequest.result;
  if (event.oldVersion < 1) {
    // New database, create "books" object store.
    db.createObjectStore("books");
  }
  if (event.oldVersion < 2) {
    // Upgrading from v1 database: add index on "title" to "books" store.
    const bookStore = openRequest.transaction.objectStore("books");
    bookStore.createIndex("by_title", "title");
  }
};

openRequest.onsuccess = () => {
  console.log(openRequest.transaction); // Will log "null".
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
- تنظیم بازه‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی داده‌ها و ایجاد تغییر در آن‌ها: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها (cursors): {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهدهٔ مثال به‌صورت زنده](https://mdn.github.io/dom-examples/to-do-notifications/))
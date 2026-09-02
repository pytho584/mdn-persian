---
title: "IDBTransaction: complete event"
short-title: complete
slug: Web/API/IDBTransaction/complete_event
page-type: web-api-event
browser-compat: api.IDBTransaction.complete_event
---

{{APIRef("IndexedDB")}}

رویداد **`complete`** در [IndexedDB API](/en-US/docs/Web/API/IndexedDB_API) زمانی شلیک می‌شود که تراکنش با موفقیت قطعی (commit) شده باشد؛ این وضعیت یا پس از فراخوانی صریح {{domxref("IDBTransaction.commit()")}} رخ می‌دهد، یا وقتی همهٔ درخواست‌ها با موفقیت تکمیل شده باشند و پس از پردازش نتایج آن‌ها، درخواست جدیدی اضافه نشده باشد. برای اطلاعات بیشتر به {{domxref("IDBTransaction")}} مراجعه کنید.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کنندهٔ رویداد تنظیم کنید.

```js-nolint
addEventListener("complete", (event) => { })

oncomplete = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

با استفاده از {{DOMxRef("EventTarget.addEventListener", "addEventListener()")}}:

```js
// Open the database
const DBOpenRequest = window.indexedDB.open("toDoList", 4);

DBOpenRequest.onupgradeneeded = (event) => {
  const db = event.target.result;

  db.onerror = () => {
    console.log("Error creating database");
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
};

DBOpenRequest.onsuccess = (event) => {
  const db = DBOpenRequest.result;

  // open a read/write db transaction, ready for adding the data
  const transaction = db.transaction(["toDoList"], "readwrite");

  // add a listener for `complete`
  transaction.addEventListener("complete", (event) => {
    console.log("Transaction was completed");
  });

  const objectStore = transaction.objectStore("toDoList");
  const newItem = {
    taskTitle: "my task",
    hours: 10,
    minutes: 10,
    day: 10,
    month: "January",
    year: 2019,
  };
  const objectStoreRequest = objectStore.add(newItem);

  objectStoreRequest.onsuccess = () => {
    // Issue a second request in the onsuccess handler,
    // so we can run this request after the first one completes,
    // while still reusing the same transaction
    const getAllRequest = objectStore.getAll();

    getAllRequest.onsuccess = () => {
      // No more requests, so the transaction completes after running this handler
      console.log(getAllRequest.result);
    };
  };
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Using IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
---
title: "IDBRequest: error event"
short-title: error
slug: Web/API/IDBRequest/error_event
page-type: web-api-event
browser-compat: api.IDBRequest.error_event
---

{{APIRef("IndexedDB")}}

هندلر `error` هنگامی اجرا می‌شود که یک خطا باعث شکست یک درخواست شود. در هندلر رویداد `error`، می‌توانید به خطای درخواست دسترسی داشته باشید و همچنین درخواست‌های بیشتری به همان تراکنش اضافه کنید.

## Syntax

از نام رویداد در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی هندلر رویداد تنظیم کنید.

```js-nolint
addEventListener("error", (event) => { })

onerror = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

این مثال یک پایگاه داده را باز می‌کند و سعی به افزودن یک رکورد می‌کند، و به رویداد `error` برای عملیات `add()` گوش می‌دهد (این رویداد رخ می‌دهد اگر مثلاً یک رکورد با `taskTitle` داده شده از قبل وجود داشته باشد):

```js
// Open the database
const DBOpenRequest = window.indexedDB.open("toDoList", 4);

DBOpenRequest.addEventListener("upgradeneeded", (event) => {
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
});

DBOpenRequest.addEventListener("success", (event) => {
  const db = DBOpenRequest.result;

  // open a read/write db transaction, ready for adding the data
  const transaction = db.transaction(["toDoList"], "readwrite");
  const objectStore = transaction.objectStore("toDoList");
  const newItem = {
    taskTitle: "my task",
    hours: 10,
    minutes: 10,
    day: 10,
    month: "January",
    year: 2020,
  };

  const objectStoreRequest = objectStore.add(newItem);
  objectStoreRequest.addEventListener("error", () => {
    console.log(`Error adding new item: ${newItem.taskTitle}`);
  });
});
```

همان مثال، با استفاده از ویژگی `onerror` به جای `addEventListener()`:

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
  const objectStore = transaction.objectStore("toDoList");
  const newItem = {
    taskTitle: "my task",
    hours: 10,
    minutes: 10,
    day: 10,
    month: "January",
    year: 2020,
  };

  const objectStoreRequest = objectStore.add(newItem);
  objectStoreRequest.onerror = () => {
    console.log(`Error adding new item: ${newItem.taskTitle}`);
  };
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
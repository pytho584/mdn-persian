---
title: "IDBTransaction: error event"
short-title: error
slug: Web/API/IDBTransaction/error_event
page-type: web-api-event
browser-compat: api.IDBTransaction.error_event
---

{{ APIRef("IndexedDB") }}

رویداد `error` روی `IDBTransaction` زمانی شلیک می‌شود که یک درخواست خطا بازگرداند و رویداد به سمت شیء تراکنش حباب کند.

> [!NOTE]
> برای مدیریت تمام راه‌هایی که یک تراکنش ممکن است شکست بخورد، بهتر است به جای آن به رویداد {{domxref("IDBTransaction.abort_event", "abort")}} گوش دهید.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("error", (event) => { })

onerror = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## حباب

این رویداد به سمت {{domxref("IDBDatabase")}} حباب می‌کند. ویژگی `event.target` به شیء {{domxref('IDBTransaction')}} که در حال حباب است اشاره می‌کند.

برای اطلاعات بیشتر، [حباب رویداد](/en-US/docs/Learn_web_development/Core/Scripting/Event_bubbling) را ببینید.

## مثال‌ها

این مثال یک پایگاه داده باز می‌کند و سعی می‌کند یک رکورد اضافه کند، و به رویداد `error` برای عملیات `add()` گوش می‌دهد (این اتفاق می‌افتد اگر مثلاً یک رکورد با `taskTitle` داده شده از قبل وجود داشته باشد):

```js
// Open the database
const dBOpenRequest = window.indexedDB.open("toDoList", 4);

dBOpenRequest.onupgradeneeded = (event) => {
  const db = event.target.result;

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

dBOpenRequest.onsuccess = (event) => {
  const db = dBOpenRequest.result;

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

  transaction.addEventListener("error", () => {
    console.log(`Error adding new item: ${newItem.taskTitle}`);
  });

  const objectStoreRequest = objectStore.add(newItem);
};
```

همان مثال، با استفاده از ویژگی `onerror` به جای `addEventListener()`:

```js
// Open the database
const dBOpenRequest = window.indexedDB.open("toDoList", 4);

dBOpenRequest.onupgradeneeded = (event) => {
  const db = event.target.result;

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

dBOpenRequest.onsuccess = (event) => {
  const db = dBOpenRequest.result;

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

  transaction.onerror = () => {
    console.log(`Error adding new item: ${newItem.taskTitle}`);
  };

  const objectStoreRequest = objectStore.add(newItem);
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
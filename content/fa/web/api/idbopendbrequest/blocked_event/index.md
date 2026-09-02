---
title: "IDBOpenDBRequest: blocked event"
short-title: blocked
slug: Web/API/IDBOpenDBRequest/blocked_event
page-type: web-api-event
browser-compat: api.IDBOpenDBRequest.blocked_event
---

{{APIRef("IndexedDB")}}

هندلر «blocked» زمانی اجرا می‌شود که یک اتصال باز به یک پایگاه داده، تراکنش «versionchange» را روی همان پایگاه داده مسدود کند.

این رویداد قابل لغو نیست و انتشار نمی‌یابد.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم نمایید.

```js-nolint
addEventListener("blocked", (event) => { })

onblocked = (event) => { }
```

## نوع رویداد

یک {{domxref("IDBVersionChangeEvent")}}. از {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram("IDBVersionChangeEvent")}}

## مثال‌ها

استفاده از `addEventListener()`:

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
  // Let's try to open the same database with a higher revision version
  const req2 = indexedDB.open("toDoList", 5);

  // In this case the onblocked handler will be executed
  req2.addEventListener("blocked", () => {
    console.log("Request was blocked");
  });
};
```

استفاده از ویژگی `onblocked`:

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
  // Let's try to open the same database with a higher revision version
  const req2 = indexedDB.open("toDoList", 5);

  // In this case the onblocked handler will be executed
  req2.onblocked = () => {
    console.log("Request was blocked");
  };
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
---
title: "IDBDatabase: versionchange event"
short-title: versionchange
slug: Web/API/IDBDatabase/versionchange_event
page-type: web-api-event
browser-compat: api.IDBDatabase.versionchange_event
---

{{APIRef("IndexedDB")}}

رویداد `versionchange` زمانی رخ می‌دهد که یک تغییر در ساختار پایگاه داده (رویداد [`upgradeneeded`](/en-US/docs/Web/API/IDBOpenDBRequest/upgradeneeded_event) که روی یک [`IDBOpenDBRequest`](/en-US/docs/Web/API/IDBOpenDBRequest) ارسال می‌شود، یا [`IDBFactory.deleteDatabase`](/en-US/docs/Web/API/IDBFactory/deleteDatabase)) در جای دیگری (بیشتر احتمالاً در یک پنجره/تب دیگر روی همان رایانه) درخواست شده باشد.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("versionchange", (event) => { })

onversionchange = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

این مثال یک پایگاه داده را باز می‌کند و در صورت موفقیت، یک شنونده به `versionchange` اضافه می‌کند:

```js
// Open the database
const dBOpenRequest = window.indexedDB.open("Nonexistent", 4);

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

dBOpenRequest.addEventListener("success", (event) => {
  const db = event.target.result;
  db.addEventListener("versionchange", (event) => {
    console.log("The version of this database has changed");
  });
});
```

همان مثال، با استفاده از ویژگی کنترل‌کننده رویداد `onversionchange`:

```js
// Open the database
const dBOpenRequest = window.indexedDB.open("Nonexistent", 4);

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
  const db = event.target.result;
  db.onversionchange = (event) => {
    console.log("The version of this database has changed");
  };
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
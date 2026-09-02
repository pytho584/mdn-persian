---
title: "IDBOpenDBRequest: upgradeneeded event"
short-title: upgradeneeded
slug: Web/API/IDBOpenDBRequest/upgradeneeded_event
page-type: web-api-event
browser-compat: api.IDBOpenDBRequest.upgradeneeded_event
---

{{APIRef("IndexedDB")}}

رویداد `upgradeneeded` زمانی فعال می‌شود که تلاش برای باز کردن یک پایگاه داده با شماره نسخه‌ای بالاتر از نسخه فعلی آن صورت گیرد.

این رویداد قابل لغو نیست و انتشار نمی‌یابد.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("upgradeneeded", (event) => { })

onupgradeneeded = (event) => { }
```

## نوع رویداد

یک {{domxref("IDBVersionChangeEvent")}} که از {{domxref("Event")}} ارث‌بری می‌کند.

{{InheritanceDiagram("IDBVersionChangeEvent")}}

## مثال‌ها

این مثال یک پایگاه داده را باز می‌کند و رویداد `upgradeneeded` را با انجام هرگونه به‌روزرسانی لازم در فروشگاه شیء مدیریت می‌کند.

```js
// Open the database
const dBOpenRequest = window.indexedDB.open("toDoList", 4);

dBOpenRequest.addEventListener("upgradeneeded", (event) => {
  const db = event.target.result;
  console.log(`Upgrading to version ${db.version}`);

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
```

این همان مثال است، اما از ویژگی کنترل‌کننده رویداد `onupgradeneeded` استفاده می‌کند.

```js
// Open the database
const dBOpenRequest = window.indexedDB.open("toDoList", 4);

dBOpenRequest.onupgradeneeded = (event) => {
  const db = event.target.result;
  console.log(`Upgrading to version ${db.version}`);

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
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
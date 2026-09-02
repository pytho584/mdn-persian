---
title: "IDBRequest: success event"
short-title: success
slug: Web/API/IDBRequest/success_event
page-type: web-api-event
browser-compat: api.IDBRequest.success_event
---

{{ APIRef("IndexedDB") }}

رویداد `success` زمانی صادر می‌شود که یک `IDBRequest` با موفقیت انجام شود. در کنترل‌گر رویداد `success` می‌توانید به نتیجهٔ درخواست دسترسی داشته باشید و همچنین درخواست‌های بیشتری را به همان تراکنش اضافه کنید.

این رویداد قابل لغو نیست و به‌صورت حبابی (bubbling) به عناصر والد منتشر نمی‌شود.

## سینتکس

از نام رویداد در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌گر رویداد (event handler property) را تنظیم کنید.

```js-nolint
addEventListener("success", (event) => { })

onsuccess = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

این مثال تلاش می‌کند یک پایگاه‌داده را باز کند و با استفاده از `addEventListener()` به رویداد `success` گوش دهد:

```js
// Open the database
const openRequest = window.indexedDB.open("toDoList", 4);

openRequest.onupgradeneeded = (event) => {
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

openRequest.addEventListener("success", (event) => {
  console.log("Database opened successfully!");
});
```

همین مثال، اما با استفاده از ویژگی کنترل‌گر رویداد `onsuccess`:

```js
// Open the database
const openRequest = window.indexedDB.open("toDoList", 4);

openRequest.onupgradeneeded = (event) => {
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

openRequest.onsuccess = (event) => {
  console.log("Database opened successfully!");
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
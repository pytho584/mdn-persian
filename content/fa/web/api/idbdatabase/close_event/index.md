---
title: "IDBDatabase: close event"
---

---
title: "IDBDatabase: close event"
short-title: close
slug: Web/API/IDBDatabase/close_event
page-type: web-api-event
browser-compat: api.IDBDatabase.close_event
---

{{ APIRef("IndexedDB") }}

رویداد `close` روی `IDBDatabase` وقتی که اتصال پایگاه داده به طور غیرمنتظره بسته شود، فعال می‌گردد. این ممکن است مثلاً زمانی رخ دهد که ذخیره‌سازی زیرین حذف شود یا کاربر پایگاه داده را در تنظیمات تاریخچه مرورگر پاک کند. توجه داشته باشید که اگر اتصال پایگاه داده به طور عادی با استفاده از [`IDBDatabase.close()`](/en-US/docs/Web/API/IDBDatabase/close) بسته شود، این رویداد فعال نمی‌شود.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم نمایید.

```js-nolint
addEventListener("close", (event) => { })

onclose = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## نمونه‌ها

این مثال یک پایگاه داده را باز می‌کند و به رویداد `close` گوش می‌دهد:

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
  db.addEventListener("close", () => {
    console.log("Database connection closed");
  });
};
```

همان مثال، با استفاده از ویژگی `onclose` به جای `addEventListener()`:

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
  db.onclose = () => {
    console.log("Database connection closed");
  };
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
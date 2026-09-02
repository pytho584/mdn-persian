---
title: "IDBDatabase: name property"
short-title: name
slug: Web/API/IDBDatabase/name
page-type: web-api-instance-property
browser-compat: api.IDBDatabase.name
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

ویژگی فقط‌خواندنیِ **`name`** از رابط `IDBDatabase` رشته‌ای است که نام پایگاه‌داده‌ی متصل را نگه می‌دارد.

## مقدار

رشته‌ای شامل نام پایگاه‌داده‌ی متصل.

## مثال‌ها

این مثال نشان می‌دهد که چگونه یک اتصال به پایگاه‌داده باز می‌شود، آبجکت {{domxref("IDBDatabase")}} حاصل در متغیر `db` ذخیره می‌گردد و سپس ویژگی `name` در کنسول ثبت می‌شود. برای مثال کامل، برنامه‌ی [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) را ببینید ([مشاهده‌ی نسخه‌ی زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).

```js
// Let us open our database
const DBOpenRequest = window.indexedDB.open("toDoList", 4);

// these two event handlers act on the database being
// opened successfully, or not
DBOpenRequest.onerror = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Error loading database.";
};

DBOpenRequest.onsuccess = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Database initialized.";

  // store the result of opening the database in the db variable. This is used a lot below
  db = DBOpenRequest.result;

  // This line will log the name of the database, which should be "toDoList"
  console.log(db.name);
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
- تنظیم محدوده‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌ها: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده‌ی مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
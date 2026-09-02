---
title: "IDBDatabase: version property"
short-title: version
slug: Web/API/IDBDatabase/version
page-type: web-api-instance-property
browser-compat: api.IDBDatabase.version
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

ویژگی **`version`** از رابط {{domxref("IDBDatabase")}} یک عدد صحیح ۶۴-بیتی است که نسخهٔ پایگاه‌دادهٔ متصل را نگه می‌دارد. زمانی که یک پایگاه‌داده برای نخستین بار ساخته می‌شود، این ویژگی یک رشتهٔ خالی است.

## مقدار

یک عدد صحیح شامل نسخهٔ پایگاه‌دادهٔ متصل.

## مثال‌ها

```js
// Let us open our database
const DBOpenRequest = window.indexedDB.open("toDoList", 4);

// these two event handlers act on the database
// being opened successfully, or not
DBOpenRequest.onerror = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Error loading database.";
};

DBOpenRequest.onsuccess = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Database initialized.";

  // store the result of opening the database in the db variable. This is used a lot below
  db = DBOpenRequest.result;

  // This line will log the version of the connected database, which should be "4"
  console.log(db.version);
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
- تنظیم بازهٔ کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و اعمال تغییر روی داده‌ها: {{domxref("IDBObjectStore")}}
- استفاده از مکان‌نماها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهدهٔ مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
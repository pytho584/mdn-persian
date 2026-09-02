---
title: "IDBDatabase: objectStoreNames property"
short-title: objectStoreNames
slug: Web/API/IDBDatabase/objectStoreNames
page-type: web-api-instance-property
browser-compat: api.IDBDatabase.objectStoreNames
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`objectStoreNames`** در رابط {{domxref("IDBDatabase")}} یک {{ domxref("DOMStringList") }} است که شامل فهرستی از نام [object store‌ها](/en-US/docs/Web/API/IndexedDB_API/Basic_Terminology#object_store) موجود در پایگاه‌داده‌ی متصل است.

## مقدار

یک {{ domxref("DOMStringList") }} شامل فهرستی از نام [object store‌ها](/en-US/docs/Web/API/IndexedDB_API/Basic_Terminology#object_store) که در حال حاضر در پایگاه‌داده‌ی متصل وجود دارند.

## مثال‌ها

```js
// Let us open our database
const DBOpenRequest = window.indexedDB.open("toDoList", 4);

// these two event handlers act on the database being opened successfully, or not
DBOpenRequest.onerror = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Error loading database.";
};

DBOpenRequest.onsuccess = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Database initialized.";

  // store the result of opening the database in the db variable. This is used a lot below
  db = DBOpenRequest.result;

  // This line will log the names of the object stores of the connected database, which should be
  // an object that looks like { ['my-store-name'] }
  console.log(db.objectStoreNames);
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم بازه‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌ها: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده‌ی مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
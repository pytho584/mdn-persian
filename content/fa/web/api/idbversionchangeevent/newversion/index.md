---
title: "IDBVersionChangeEvent: newVersion property"
short-title: newVersion
slug: Web/API/IDBVersionChangeEvent/newVersion
page-type: web-api-instance-property
browser-compat: api.IDBVersionChangeEvent.newVersion
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

خاصیت فقط-خواندنی **`newVersion`** از رابط {{domxref("IDBVersionChangeEvent")}} شماره نسخه جدید پایگاه داده را برمی‌گرداند.

## مقدار

یک عدد که یک عدد صحیح ۶۴-بیتی است، یا اگر پایگاه داده در حال حذف شدن باشد، `null` است.

## مثال‌ها

در قطعه کد زیر، ما یک درخواست برای باز کردن یک پایگاه داده می‌فرستیم و handlerهایی برای موارد موفقیت و خطا اضافه می‌کنیم. این رویدادها از طریق رابط سفارشی `IDBVersionChangeEvent` شلیک می‌شوند. برای یک مثال کامل و کارآمد، به برنامه [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ما مراجعه کنید ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).

```js
const note = document.querySelector("ul");

// Let us open version 4 of our database
const DBOpenRequest = window.indexedDB.open("toDoList", 4);

// these two event handlers act on the database being opened
DBOpenRequest.onerror = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Error loading database.";
};

DBOpenRequest.onsuccess = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Database initialized.";

  // store the result of opening the database in the db variable.
  // This is used a lot later on, for opening transactions and suchlike.
  const db = DBOpenRequest.result;
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم بازه‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌هایتان: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
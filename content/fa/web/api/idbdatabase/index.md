---
title: IDBDatabase
slug: Web/API/IDBDatabase
page-type: web-api-interface
browser-compat: api.IDBDatabase
---

{{APIRef("IndexedDB")}} {{AvailableInWorkers}}

رابط **`IDBDatabase`** در API IndexedDB یک [اتصال به پایگاه داده](/en-US/docs/Web/API/IndexedDB_API/Basic_Terminology#database_connection) فراهم می‌کند؛ می‌توانید از یک شیء `IDBDatabase` برای باز کردن یک [تراکنش](/en-US/docs/Web/API/IndexedDB_API/Basic_Terminology#transaction) روی پایگاه داده استفاده کنید و سپس اشیاء (داده‌ها) را در آن پایگاه داده ایجاد، دستکاری، و حذف کنید. این رابط تنها راه دریافت و مدیریت نسخه‌های پایگاه داده است.

> [!NOTE]
> هر کاری که در IndexedDB انجام می‌دهید همیشه در بستر یک [تراکنش](/en-US/docs/Web/API/IndexedDB_API/Basic_Terminology#transaction) صورت می‌گیرد که تعامل با داده‌ها در پایگاه داده را نشان می‌دهد. همه اشیاء در IndexedDB — از جمله object storeها، ایندکس‌ها و cursorها — به یک تراکنش خاص وابسته هستند. بنابراین، نمی‌توانید خارج از یک تراکنش دستوری اجرا کنید، به داده‌ای دسترسی پیدا کنید، یا چیزی را باز کنید.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("IDBDatabase.name")}} {{ReadOnlyInline}}
  - : یک رشته (string) که نام پایگاه داده متصل شده را در بر دارد.
- {{domxref("IDBDatabase.version")}} {{ReadOnlyInline}}
  - : یک عدد صحیح ۶۴-بیتی که نسخه پایگاه داده متصل شده را شامل می‌شود. وقتی یک پایگاه داده برای اولین بار ایجاد می‌شود، این ویژگی یک رشته خالی است.
- {{domxref("IDBDatabase.objectStoreNames")}} {{ReadOnlyInline}}
  - : یک {{ domxref("DOMStringList") }} که فهرستی از نام [object storeها](/en-US/docs/Web/API/IndexedDB_API/Basic_Terminology#object_store) موجود در پایگاه داده متصل شده را شامل می‌شود.

## متدهای نمونه

ارث‌بری از: [EventTarget](/en-US/docs/Web/API/EventTarget)

- {{domxref("IDBDatabase.close()")}}
  - : بلافاصله بازمی‌گردد و اتصال به پایگاه داده را در یک نخ (thread) جداگانه می‌بندد.
- {{domxref("IDBDatabase.createObjectStore()")}}
  - : یک object store یا ایندکس جدید ایجاد کرده و آن را بازمی‌گرداند.
- {{domxref("IDBDatabase.deleteObjectStore()")}}
  - : object store با نام داده‌شده در پایگاه داده متصل را همراه با هر ایندکسی که به آن ارجاع می‌دهد، از بین می‌برد.
- {{domxref("IDBDatabase.transaction()")}}
  - : بلافاصله یک شیء تراکنش ({{domxref("IDBTransaction")}}) شامل متد {{domxref("IDBTransaction.objectStore")}} بازمی‌گرداند که می‌توانید از آن برای دسترسی به object store خود استفاده کنید. در یک نخ جداگانه اجرا می‌شود.

## رویدادها

برای گوش دادن به این رویدادها می‌توانید از `addEventListener()` استفاده کنید یا یک شنونده رویداد را به ویژگی `oneventname` این رابط اختصاص دهید.

- [`close`](/en-US/docs/Web/API/IDBDatabase/close_event)
  - : رویدادی که هنگام بسته شدن غیرمنتظره اتصال پایگاه داده رخ می‌دهد.

- [`versionchange`](/en-US/docs/Web/API/IDBDatabase/versionchange_event)
  - : رویدادی که هنگام درخواست تغییر ساختار پایگاه داده رخ می‌دهد.

رویدادهای زیر از طریق رویداد bubbling (بالارونده) از {{domxref("IDBTransaction")}} در دسترس `IDBDatabase` قرار می‌گیرند:

- `IDBTransaction` [`abort`](/en-US/docs/Web/API/IDBTransaction/abort_event)
  - : رویدادی که هنگام لغو (abort) شدن یک تراکنش رخ می‌دهد.
- `IDBTransaction` [`error`](/en-US/docs/Web/API/IDBTransaction/error_event)
  - : رویدادی که وقتی یک درخواست خطا برمی‌گرداند و رویداد به سمت شیء اتصال بالا می‌آید، رخ می‌دهد.

## مثال

در قطعه کد زیر، یک پایگاه داده را به‌صورت ناهمگام (asynchronous) باز می‌کنیم ({{domxref("IDBFactory")}})، موارد موفقیت و خطا را مدیریت می‌کنیم، و در صورت نیاز به ارتقا، یک object store جدید ایجاد می‌کنیم (`IDBDatabase`). برای یک مثال کامل و قابل اجرا، برنامه [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) را ببینید ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).

```js
// Let us open our database
const DBOpenRequest = window.indexedDB.open("toDoList", 4);

// these two event handlers act on the IDBDatabase object,
// when the database is opened successfully, or not
DBOpenRequest.onerror = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Error loading database.";
};

DBOpenRequest.onsuccess = (event) => {
  node.appendChild(document.createElement("li")).textContent =
    "Database initialized.";

  // store the result of opening the database in the db
  // variable. This is used a lot later on
  db = DBOpenRequest.result;

  // Run the displayData() function to populate the task
  // list with all the to-do list data already in the IDB
  displayData();
};

// This event handles the event whereby a new version of
// the database needs to be created Either one has not
// been created before, or a new version number has been
// submitted via the window.indexedDB.open line above

DBOpenRequest.onupgradeneeded = (event) => {
  const db = event.target.result;

  db.onerror = (event) => {
    note.appendChild(document.createElement("li")).textContent =
      "Error loading database.";
  };

  // Create an objectStore for this database using
  // IDBDatabase.createObjectStore

  const objectStore = db.createObjectStore("toDoList", {
    keyPath: "taskTitle",
  });

  // define what data items the objectStore will contain

  objectStore.createIndex("hours", "hours", { unique: false });
  objectStore.createIndex("minutes", "minutes", { unique: false });
  objectStore.createIndex("day", "day", { unique: false });
  objectStore.createIndex("month", "month", { unique: false });
  objectStore.createIndex("year", "year", { unique: false });

  objectStore.createIndex("notified", "notified", { unique: false });

  note.appendChild(document.createElement("li")).textContent =
    "Object store created.";
};
```

این خط بعدی یک تراکنش روی پایگاه داده باز می‌کند، سپس یک object store باز می‌کند که می‌توانیم داده‌های داخل آن را دستکاری کنیم.

```js
const objectStore = db
  .transaction("toDoList", "readwrite")
  .objectStore("toDoList");
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- کار با تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم محدوده کلیدها: {{domxref("IDBKeyRange")}}
- دریافت داده‌ها و ایجاد تغییرات در آن‌ها: {{domxref("IDBObjectStore")}}
- کار با cursorها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
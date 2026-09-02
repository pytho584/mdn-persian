---
title: "IDBOpenDBRequest"
---

---
title: IDBOpenDBRequest
slug: Web/API/IDBOpenDBRequest
page-type: web-api-interface
browser-compat: api.IDBOpenDBRequest
---

{{APIRef("IndexedDB")}} {{AvailableInWorkers}}

رابط **`IDBOpenDBRequest`** در API IndexedDB، دسترسی به نتایج درخواست‌های باز کردن یا حذف پایگاه داده را از طریق ویژگی‌های مخصوص رویدادگردان فراهم می‌کند (این درخواست‌ها با استفاده از {{domxref("IDBFactory.open")}} و {{domxref("IDBFactory.deleteDatabase")}} انجام می‌شوند).

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_همچنین ویژگی‌های والدهای خود، {{domxref("IDBRequest")}} و {{domxref("EventTarget")}} را به ارث می‌برد._

## متدهای نمونه

_متدی ندارد، اما متدهای والدهای خود، {{domxref("IDBRequest")}} و {{domxref("EventTarget")}} را به ارث می‌برد._

## رویدادها

_رویدادهایی که در رابط‌های والد، {{DOMxRef("IDBRequest")}} و {{DOMxRef("EventTarget")}} تعریف شده‌اند، می‌توانند روی اشیاء `IDBOpenDBRequest` نیز ارسال شوند._

برای گوش دادن به این رویدادهای عمومی و اختصاصی، از `addEventListener()` استفاده کنید یا یک شنوندهٔ رویداد را به ویژگی `oneventname` این رابط اختصاص دهید.

رویدادهای مختص این رابط عبارت‌اند از:

- [`blocked`](/en-US/docs/Web/API/IDBOpenDBRequest/blocked_event)
  - : زمانی رخ می‌دهد که یک اتصال باز به یک پایگاه داده، تراکنش `versionchange` روی همان پایگاه داده را مسدود کرده باشد. همچنین از طریق ویژگی [`onblocked`](/en-US/docs/Web/API/IDBOpenDBRequest/blocked_event) در دسترس است.
- [`upgradeneeded`](/en-US/docs/Web/API/IDBOpenDBRequest/upgradeneeded_event)
  - : زمانی رخ می‌دهد که تلاشی برای باز کردن یک پایگاه داده با شماره نسخه‌ای بالاتر از نسخه فعلی آن انجام شود. همچنین از طریق ویژگی [`onupgradeneeded`](/en-US/docs/Web/API/IDBOpenDBRequest/upgradeneeded_event) در دسترس است.

## مثال

در مثال زیر، می‌بینید که از گردانندهٔ رویداد onupgradeneeded برای به‌روزرسانی ساختار پایگاه داده استفاده می‌شود، در صورتی که پایگاه داده‌ای با شماره نسخه بالاتر بارگذاری شود. برای مشاهده یک مثال کامل و قابل اجرا، به برنامه [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) مراجعه کنید ([مشاهده مثال به‌صورت زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).

```js
let db;

// Let us open our database
const DBOpenRequest = window.indexedDB.open("toDoList", 4);

// these event handlers act on the database being opened.
DBOpenRequest.onerror = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Error loading database.";
};

DBOpenRequest.onsuccess = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Database initialized.";

  // store the result of opening the database in the db
  // variable. This is used a lot below
  db = DBOpenRequest.result;

  // Run the displayData() function to populate the task
  // list with all the to-do list data already in the IDB
  displayData();
};

// This event handles the event whereby a new version of
// the database needs to be created Either one has not
// been created before, or a new version number has been
// submitted via the window.indexedDB.open line above
// it is only implemented in recent browsers
DBOpenRequest.onupgradeneeded = (event) => {
  const db = event.target.result;

  db.onerror = (event) => {
    note.appendChild(document.createElement("li")).textContent =
      "Error loading database.";
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
  objectStore.createIndex("notified", "notified", { unique: false });
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
- تنظیم بازه‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌ها: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده نسخه زنده مثال](https://mdn.github.io/dom-examples/to-do-notifications/)).
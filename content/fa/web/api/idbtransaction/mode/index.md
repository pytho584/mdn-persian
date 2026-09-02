---
title: "IDBTransaction: mode property"
short-title: mode
slug: Web/API/IDBTransaction/mode
page-type: web-api-instance-property
browser-compat: api.IDBTransaction.mode
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

ویژگی فقط‑خواندنی **`mode`** از رابط {{domxref("IDBTransaction")}} حالت فعلی دسترسی به داده‌ها در ذخیره‌گاه‌های شیء (object stores) در محدودهٔ تراکنش را برمی‌گرداند (یعنی آیا حالت فقط‑خواندنی است یا می‌خواهید در ذخیره‌گاه‌های شیء بنویسید؟). مقدار پیش‌فرض `readonly` است.

## مقدار

یک رشته که حالت جداسازی دسترسی به داده‌ها در ذخیره‌گاه‌های شیء فعلی را تعریف می‌کند. مقادیر زیر در دسترس هستند:

- `readonly`
  - : اجازه می‌دهد داده‌ها خوانده شوند اما تغییر نکنند.
- `readwrite`
  - : اجازه خواندن و نوشتن داده‌ها در ذخیره‌گاه‌های داده موجود را می‌دهد.
- `versionchange`
  - : اجازه هر عملیاتی، از جمله عملیات حذف و ایجاد ذخیره‌گاه‌های شیء و ایندکس‌ها را می‌دهد. این حالت برای به‌روزرسانی شماره نسخه تراکنش‌ها در صورت تشخیص نیاز هنگام فراخوانی {{domxref("IDBFactory.open()")}} استفاده می‌شود. تراکنش‌های این حالت نمی‌توانند همزمان با سایر تراکنش‌ها اجرا شوند. تراکنش‌های در این حالت به عنوان _تراکنش‌های ارتقا_ (upgrade transactions) شناخته می‌شوند.

## مثال‌ها

در قطعه کد زیر، یک تراکنش خواندن/نوشتن روی پایگاه داده خود باز می‌کنیم و داده‌هایی را به یک ذخیره‌گاه شیء اضافه می‌کنیم. همچنین به توابع متصل شده به رویدادگردان‌های تراکنش توجه کنید که نتیجه باز شدن تراکنش را در صورت موفقیت یا شکست گزارش می‌دهند. در پایان، حالت تراکنش فعلی را با استفاده از `mode` ثبت می‌کنیم. برای یک مثال کامل کار، به [برنامه اعلان‌های کارهای روزانه](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) مراجعه کنید ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).

```js
const note = document.getElementById("notifications");

// یک نمونه از شیء db برای ذخیره داده‌های IDB
let db;

// پایگاه داده خود را باز می‌کنیم
const DBOpenRequest = window.indexedDB.open("toDoList", 4);

DBOpenRequest.onsuccess = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Database initialized.";

  // نتیجه باز شدن پایگاه داده را در متغیر db ذخیره می‌کنیم
  db = DBOpenRequest.result;

  // تابع addData() را برای افزودن داده به پایگاه داده اجرا می‌کنیم
  addData();
};

function addData() {
  // یک شیء جدید برای درج در IDB ایجاد می‌کنیم
  const newItem = [
    {
      taskTitle: "Walk dog",
      hours: 19,
      minutes: 30,
      day: 24,
      month: "December",
      year: 2013,
      notified: "no",
    },
  ];

  // یک تراکنش خواندن/نوشتن برای افزودن داده باز می‌کنیم
  const transaction = db.transaction(["toDoList"], "readwrite");

  // گزارش موفقیت باز شدن تراکنش
  transaction.oncomplete = (event) => {
    note.appendChild(document.createElement("li")).textContent =
      "Transaction completed: database modification finished.";
  };

  transaction.onerror = (event) => {
    note.appendChild(document.createElement("li")).textContent =
      "Transaction not opened due to error. Duplicate items not allowed.";
  };

  // یک ذخیره‌گاه شیء روی تراکنش ایجاد می‌کنیم
  const objectStore = transaction.objectStore("toDoList");

  // شیء newItem را به ذخیره‌گاه شیء اضافه می‌کنیم
  const objectStoreRequest = objectStore.add(newItem[0]);

  objectStoreRequest.onsuccess = (event) => {
    // گزارش موفقیت درخواست (این به معنای ذخیره موفق در پایگاه داده نیست؛ برای آن باید transaction.onsuccess را بررسی کنید)
    note.appendChild(document.createElement("li")).textContent =
      "Request successful.";
  };

  // حالت تراکنش باز شده را برمی‌گردانیم (در اینجا باید "readwrite" باشد)
  transaction.mode;
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم محدوده کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌هایتان: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها: {{domxref("IDBCursor")}}
- مثال مرجع: [اعلان‌های کارهای روزانه](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/))
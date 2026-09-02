---
title: "IDBObjectStore: transaction property"
short-title: transaction
slug: Web/API/IDBObjectStore/transaction
page-type: web-api-instance-property
browser-compat: api.IDBObjectStore.transaction
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

خاصیت فقط-خواندنی **`transaction`** در رابط {{domxref("IDBObjectStore")}}، شیء تراکنشی را برمی‌گرداند که این object store به آن تعلق دارد.

## مقدار

یک شیء {{domxref("IDBTransaction")}}.

## مثال‌ها

در قطعه کد زیر، یک تراکنش خواندن/نوشتن روی پایگاه داده خود باز می‌کنیم و با استفاده از `add()` داده‌هایی را به یک object store اضافه می‌کنیم. پس از ایجاد object store، مقدار `objectStore.transaction` را در کنسول ثبت می‌کنیم. برای یک مثال کامل کاربردی، به برنامه [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ما مراجعه کنید ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).

```js
// اجازه دهید پایگاه داده خود را باز کنیم
const DBOpenRequest = window.indexedDB.open("toDoList", 4);

DBOpenRequest.onsuccess = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "پایگاه داده مقداردهی اولیه شد.";

  // نتیجه باز کردن پایگاه داده را در متغیر db ذخیره کنید.
  // این متغیر در ادامه بسیار استفاده می‌شود
  db = DBOpenRequest.result;

  // تابع addData() را برای افزودن داده به پایگاه داده اجرا کنید
  addData();
};

function addData() {
  // یک شیء جدید آماده برای درج در IDB ایجاد کنید
  const newItem = [
    {
      taskTitle: "سگ را قدم بزن",
      hours: 19,
      minutes: 30,
      day: 24,
      month: "دسامبر",
      year: 2013,
      notified: "خیر",
    },
  ];

  // یک تراکنش خواندن/نوشتن روی پایگاه داده باز کنید، آماده برای افزودن داده
  const transaction = db.transaction(["toDoList"], "readwrite");

  // پس از اتمام کار، موفقیت کامل شدن تراکنش را گزارش دهید
  transaction.oncomplete = (event) => {
    note.appendChild(document.createElement("li")).textContent =
      "تراکنش کامل شد.";
  };

  transaction.onerror = (event) => {
    note.appendChild(document.createElement("li")).textContent =
      "تراکنش به دلیل خطا باز نشد. موارد تکراری مجاز نیستند.";
  };

  // یک object store روی تراکنش ایجاد کنید
  const objectStore = transaction.objectStore("toDoList");
  console.log(objectStore.transaction);

  // یک درخواست برای افزودن شیء newItem به object store ایجاد کنید
  const objectStoreRequest = objectStore.add(newItem[0]);

  objectStoreRequest.onsuccess = (event) => {
    // موفقیت درخواست خود را گزارش دهید
    note.appendChild(document.createElement("li")).textContent =
      "درخواست موفقیت‌آمیز بود.";
  };
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم محدوده کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌های خود: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
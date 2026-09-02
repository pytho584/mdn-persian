---
title: "IDBTransaction: error property"
short-title: error
slug: Web/API/IDBTransaction/error
page-type: web-api-instance-property
browser-compat: api.IDBTransaction.error
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

خاصیت **`IDBTransaction.error`** از رابط {{domxref("IDBTransaction")}}، نوع خطا را در هنگام ناقص ماندن تراکنش بازمی‌گرداند.

## مقدار

یک {{domxref("DOMException")}} حاوی خطای مربوطه، یا `null` در صورت عدم وجود خطا.

این می‌تواند ارجاعی به همان خطای شیء درخواستی باشد که آن را ایجاد کرده، یا یک شکست تراکنش (مثلاً `QuotaExceededError`).

این خاصیت زمانی `null` است که تراکنش هنوز به پایان نرسیده، یا به پایان رسیده و با موفقیت commit شده است.

## مثال‌ها

در قطعه کد زیر، یک تراکنش خواندن/نوشتن روی پایگاه داده خود باز می‌کنیم و داده‌هایی را به یک object store اضافه می‌کنیم. همچنین به توابع متصل به رویدادهای تراکنش توجه کنید که نتیجه باز شدن تراکنش را در صورت موفقیت یا شکست گزارش می‌دهند. به بلوک `transaction.onerror = (event) => { };` توجه کنید که از `transaction.error` برای کمک به گزارش مشکل در هنگام ناموفق بودن تراکنش استفاده می‌کند. برای یک مثال کامل کارکردی، برنامه [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ما را ببینید ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).

```js
const note = document.getElementById("notifications");

// یک نمونه از شیء db برای ذخیره داده‌های IDB
let db;

// بیایید پایگاه داده خود را باز کنیم
const DBOpenRequest = window.indexedDB.open("toDoList", 4);

DBOpenRequest.onsuccess = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "پایگاه داده مقداردهی اولیه شد.";

  // نتیجه باز کردن پایگاه داده را در متغیر db ذخیره کنید.
  // این در ادامه زیاد استفاده می‌شود
  db = DBOpenRequest.result;

  // تابع addData() را برای افزودن داده به پایگاه داده اجرا کنید
  addData();
};

function addData() {
  // یک شیء جدید برای درج در IDB ایجاد کنید
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

  // یک تراکنش خواندن/نوشتن db باز کنید، آماده برای افزودن داده
  const transaction = db.transaction(["toDoList"], "readwrite");

  // موفقیت باز شدن تراکنش را گزارش دهید
  transaction.oncomplete = (event) => {
    note.appendChild(document.createElement("li")).textContent =
      "تراکنش کامل شد: تغییرات پایگاه داده به پایان رسید.";
  };

  transaction.onerror = (event) => {
    note.appendChild(document.createElement("li")).textContent =
      `تراکنش به دلیل خطا باز نشد: ${transaction.error}`;
  };

  // یک object store روی تراکنش ایجاد کنید
  const objectStore = transaction.objectStore("toDoList");

  // شیء newItem خود را به object store اضافه کنید
  const objectStoreRequest = objectStore.add(newItem[0]);

  objectStoreRequest.onsuccess = (event) => {
    // موفقیت درخواست را گزارش دهید (این به معنای ذخیره موفقیت‌آمیز آیتم در DB نیست - برای آن نیاز به transaction.onsuccess دارید)
    note.appendChild(document.createElement("li")).textContent =
      "درخواست موفقیت‌آمیز بود.";
  };
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
- بازیابی و ایجاد تغییرات در داده‌ها: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
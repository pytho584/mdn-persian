---
title: "IDBVersionChangeEvent"
slug: Web/API/IDBVersionChangeEvent
page-type: web-api-interface
browser-compat: api.IDBVersionChangeEvent
---

{{APIRef("IndexedDB")}} {{AvailableInWorkers}}

رابط **`IDBVersionChangeEvent`** در [API IndexedDB](/en-US/docs/Web/API/IndexedDB_API) نشان‌دهنده تغییر نسخه پایگاه داده است که در نتیجه اجرای تابع رویدادگردان {{domxref("IDBOpenDBRequest.upgradeneeded_event", "onupgradeneeded")}} رخ می‌دهد.

{{InheritanceDiagram}}

## سازنده

- {{domxref("IDBVersionChangeEvent.IDBVersionChangeEvent", "IDBVersionChangeEvent()")}}
  - : یک شیء جدید `IDBVersionChangeEvent` ایجاد و برمی‌گرداند که برای نمایش تغییر نسخه پایگاه داده استفاده می‌شود.

## ویژگی‌های نمونه

_همچنین ویژگی‌هایی را از والد خود، یعنی رابط {{domxref("Event")}}، به ارث می‌برد._

- {{ domxref("IDBVersionChangeEvent.oldVersion") }} {{ReadOnlyInline}}
  - : نسخه قدیمی پایگاه داده را برمی‌گرداند.
- {{ domxref("IDBVersionChangeEvent.newVersion") }} {{ReadOnlyInline}}
  - : نسخه جدید پایگاه داده را برمی‌گرداند.

## روش‌های نمونه

_روش اختصاصی ندارد، اما روش‌های والد خود، یعنی رابط {{domxref("Event")}}، را به ارث می‌برد._

## مثال

در قطعه کد زیر، یک درخواست برای باز کردن پایگاه داده ارسال می‌کنیم و برای موارد موفقیت و خطا، رویدادگردان‌هایی تعریف می‌کنیم. پس از تغییر نسخه (پس از رویداد `upgradeneeded`)، رویداد `success` رابط `IDBVersionChangeEvent` را پیاده‌سازی می‌کند. برای یک مثال کامل و عملی، برنامه [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) را مشاهده کنید ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).

```js
const note = document.querySelector("ul");

// بیایید نسخه ۴ پایگاه داده خود را باز کنیم
const DBOpenRequest = window.indexedDB.open("toDoList", 4);

// این دو رویدادگردان به موفقیت‌آمیز بودن یا نبودن باز شدن پایگاه داده واکنش نشان می‌دهند
DBOpenRequest.onerror = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "خطا در بارگذاری پایگاه داده.";
};

DBOpenRequest.onsuccess = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "پایگاه داده مقداردهی اولیه شد.";

  // نتیجه باز کردن پایگاه داده را در متغیر db ذخیره می‌کنیم. این متغیر بعداً برای باز کردن تراکنش‌ها و موارد مشابه بسیار استفاده می‌شود.
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
- تنظیم محدوده کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌ها: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
---
title: "IDBFactory: open() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/IDBFactory/open"
---

---
title: "IDBFactory: open() method"
short-title: open()
slug: Web/API/IDBFactory/open
page-type: web-api-instance-method
browser-compat: api.IDBFactory.open
---

{{APIRef("IndexedDB")}} {{AvailableInWorkers}}

متد **`open()`** از واسط {{domxref("IDBFactory")}} درخواست باز کردن یک [اتصال به پایگاه داده](/en-US/docs/Web/API/IndexedDB_API/Basic_Terminology#database_connection) را می‌دهد.

این متد بلافاصله یک شیء {{domxref("IDBOpenDBRequest")}} برمی‌گرداند و عملیات باز کردن را به صورت ناهمگام (async) انجام می‌دهد. اگر عملیات موفقیت‌آمیز باشد، یک رویداد `success` روی شیء درخواست که از این متد برگردانده شده است، شلیک می‌شود و ویژگی `result` آن به شیء جدید {{domdesc("IDBDatabase")}} برای اتصال تنظیم می‌گردد.

ممکن است رویدادهای `upgradeneeded`، `blocked` یا `versionchange` را نیز راه‌اندازی کند.

## نحو (Syntax)

```js-nolint
open(name)
open(name, version)
```

### پارامترها

- `name`
  - : نام پایگاه داده.
- `version` {{optional_inline}}
  - : اختیاری. نسخه‌ای که پایگاه داده با آن باز شود. اگر نسخه ارائه نشود و پایگاه داده وجود داشته باشد، یک اتصال به پایگاه داده بدون تغییر نسخه آن باز می‌شود. اگر نسخه ارائه نشود و پایگاه داده وجود نداشته باشد، با نسخه `1` ایجاد می‌شود.

### مقدار بازگشتی

یک شیء {{domxref("IDBOpenDBRequest")}} که رویدادهای مرتبط با این درخواست روی آن شلیک می‌شوند. اگر عملیات موفقیت‌آمیز باشد، مقدار ویژگی {{domxref("IDBRequest.result", "result")}} درخواست، یک شیء {{domxref("IDBDatabase")}} است که نشان‌دهنده اتصال به پایگاه داده می‌باشد.

### استثناها (Exceptions)

- {{jsxref("TypeError")}}
  - : اگر مقدار `version` عددی بزرگتر از صفر نباشد، پرتاب می‌شود.

## مثال‌ها

مثالی از فراخوانی `open` با پارامتر `version` مطابق مشخصات فعلی:

```js
const request = window.indexedDB.open("toDoList", 4);
```

در قطعه کد زیر، ما یک درخواست برای باز کردن پایگاه داده ارائه می‌دهیم و کنترل‌کننده‌هایی برای موارد موفقیت و خطا قرار می‌دهیم. برای یک مثال کامل کار، به برنامه [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ما مراجعه کنید ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).

```js
const note = document.querySelector("ul");

// بیایید نسخه 4 پایگاه داده خود را باز کنیم
const DBOpenRequest = window.indexedDB.open("toDoList", 4);

// این دو کنترل‌کننده رویداد روی باز شدن موفق یا ناموفق پایگاه داده عمل می‌کنند
DBOpenRequest.onerror = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "خطا در بارگذاری پایگاه داده.";
};

DBOpenRequest.onsuccess = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "پایگاه داده مقداردهی اولیه شد.";

  // نتیجه باز کردن پایگاه داده را در متغیر db ذخیره کنید.
  // بعداً برای باز کردن تراکنش‌ها و موارد مشابه بسیار استفاده می‌شود.
  db = DBOpenRequest.result;
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- [محدودیت‌های ذخیره‌سازی مرورگر و معیارهای حذف](/en-US/docs/Web/API/Storage_API/Storage_quotas_and_eviction_criteria).
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم یک محدوده از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌های خود: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
---
title: IDBFactory
slug: Web/API/IDBFactory
page-type: web-api-interface
browser-compat: api.IDBFactory
---

{{APIRef("IndexedDB")}} {{AvailableInWorkers}}

رابط **`IDBFactory`** از [API IndexedDB](/en-US/docs/Web/API/IndexedDB_API) به برنامه‌ها امکان می‌دهد تا به صورت ناهمگام به پایگاه‌های داده‌ی فهرست‌بندی شده دسترسی داشته باشند. شیئی که این رابط را پیاده‌سازی می‌کند `window.indexedDB` است. شما با استفاده از این شیء، یک پایگاه داده را باز می‌کنید (یعنی ایجاد و به آن دسترسی پیدا می‌کنید) و حذف می‌کنید، نه مستقیماً با `IDBFactory`.

## روش‌های نمونه

- {{domxref("IDBFactory.open()")}}
  - : درخواست باز کردن یک [اتصال به پایگاه داده](/en-US/docs/Web/API/IndexedDB_API/Basic_Terminology#database_connection) را می‌دهد.
- {{domxref("IDBFactory.deleteDatabase()")}}
  - : درخواست حذف یک پایگاه داده را می‌دهد.
- {{domxref("IDBFactory.cmp()")}}
  - : دو کلید را با هم مقایسه می‌کند و نتیجه‌ای را برمی‌گرداند که نشان می‌دهد کدام یک از نظر مقدار بزرگ‌تر است.
- {{domxref("IDBFactory.databases()")}}
  - : یک promise برمی‌گرداند که با آرایه‌ای از تمام پایگاه‌های داده‌ی موجود، شامل نام‌ها و نسخه‌های آن‌ها، fulfilled می‌شود.

## مثال

در قطعه کد زیر، ما یک درخواست برای باز کردن یک پایگاه داده ارسال می‌کنیم و handlerهایی برای موارد موفقیت و خطا در نظر می‌گیریم. برای یک مثال کامل و عملی، به برنامه‌ی [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ما مراجعه کنید ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).

```js
// بیایید نسخه ۴ پایگاه داده خود را باز کنیم
const DBOpenRequest = window.indexedDB.open("toDoList", 4);

// این دو event handler روی باز شدن موفق یا ناموفق پایگاه داده عمل می‌کنند
DBOpenRequest.onerror = (event) => {
  console.error("خطا در بارگذاری پایگاه داده.");
};

DBOpenRequest.onsuccess = (event) => {
  console.info("پایگاه داده مقداردهی اولیه شد.");

  // نتیجه باز کردن پایگاه داده را در متغیر db ذخیره کنید. این متغیر بعداً برای باز کردن تراکنش‌ها و موارد مشابه بسیار استفاده می‌شود.
  db = DBOpenRequest.result;
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
- تنظیم محدوده‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌های خود: {{domxref("IDBObjectStore")}}
- استفاده از مکان‌نماها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
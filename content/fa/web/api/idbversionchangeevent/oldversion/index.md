---
title: "IDBVersionChangeEvent: oldVersion property"
short-title: oldVersion
slug: Web/API/IDBVersionChangeEvent/oldVersion
page-type: web-api-instance-property
browser-compat: api.IDBVersionChangeEvent.oldVersion
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

خاصیت فقط‌خواندنی **`oldVersion`** از رابط {{domxref("IDBVersionChangeEvent")}}، شمارهٔ نسخهٔ قدیمی پایگاه‌داده را برمی‌گرداند.

هنگامی که پایگاه‌دادهٔ بازشده هنوز وجود نداشته باشد، مقدار `oldVersion` برابر ۰ است.

## مقدار

یک عدد صحیح ۶۴-بیتی.

## مثال‌ها

```js
const dbName = "sampleDB";
const dbVersion = 2;
const request = indexedDB.open(dbName, dbVersion);

request.onupgradeneeded = (e) => {
  const db = request.result;
  if (e.oldVersion < 1) {
    db.createObjectStore("store1");
  }

  if (e.oldVersion < 2) {
    db.deleteObjectStore("store1");
    db.createObjectStore("store2");
  }

  // etc. for version < 3, 4…
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
- بازیابی و اعمال تغییرات روی داده‌ها: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهدهٔ مثال به‌صورت زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
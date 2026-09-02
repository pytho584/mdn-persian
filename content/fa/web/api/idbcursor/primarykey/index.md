---
title: "IDBCursor: primaryKey property"
short-title: primaryKey
slug: Web/API/IDBCursor/primaryKey
page-type: web-api-instance-property
browser-compat: api.IDBCursor.primaryKey
---

{{APIRef("IDBCursor")}} {{AvailableInWorkers}}

ویژگی فقط‌خواندنیِ **`primaryKey`** در رابط {{domxref("IDBCursor")}}، کلید مؤثرِ فعلیِ نشانگر (cursor) را برمی‌گرداند. اگر نشانگر در حال پیمایش باشد یا بیرون از محدودهٔ خود پیمایش کرده باشد، مقدار این ویژگی `undefined` خواهد بود. کلید اصلیِ نشانگر می‌تواند از هر نوع داده‌ای باشد.

## مقدار

مقداری از هر نوع داده.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : این خطا زمانی پرتاب می‌شود که نشانگر در حال پیشروی باشد یا پیمایش را به پایان رسانده باشد.

## مثال‌ها

در این قطعهٔ ساده، یک تراکنش می‌سازیم، یک مخزن اشیاء (object store) را بازیابی می‌کنیم و سپس با استفاده از یک نشانگر (cursor) همهٔ رکوردهای آن مخزن را پیمایش می‌کنیم. در هر بار پیمایش، کلید اصلیِ نشانگر را در کنسول ثبت می‌کنیم.

با این نشانگر نیازی نیست داده‌ها را بر پایهٔ کلید انتخاب کنیم؛ می‌توانیم همهٔ داده‌ها را یک‌جا بگیریم. همچنین توجه کنید که در هر تکرار حلقه می‌توانید داده‌های رکورد جاری را با استفاده از `cursor.value.foo` از روی شیء نشانگر بگیرید. برای یک مثال کامل و قابل اجرا، به [نمونهٔ IDBCursor](https://github.com/mdn/dom-examples/tree/main/indexeddb-examples/idbcursor) مراجعه کنید ([مشاهدهٔ نسخهٔ زندهٔ مثال](https://mdn.github.io/dom-examples/indexeddb-examples/idbcursor/)).

```js
function displayData() {
  const transaction = db.transaction(["rushAlbumList"], "readonly");
  const objectStore = transaction.objectStore("rushAlbumList");

  objectStore.openCursor().onsuccess = (event) => {
    const cursor = event.target.result;
    if (cursor) {
      const listItem = document.createElement("li");
      listItem.textContent = `${cursor.value.albumTitle}, ${cursor.value.year}`;
      list.appendChild(listItem);

      console.log(cursor.primaryKey);
      cursor.continue();
    } else {
      console.log("Entries all displayed.");
    }
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
- تنظیم بازه‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌ها: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهدهٔ نسخهٔ زندهٔ مثال](https://mdn.github.io/dom-examples/to-do-notifications/)).
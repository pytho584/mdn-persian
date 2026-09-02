---
title: "IDBCursorWithValue: value property"
---

---
title: "IDBCursorWithValue: value property"
short-title: value
slug: Web/API/IDBCursorWithValue/value
page-type: web-api-instance-property
browser-compat: api.IDBCursorWithValue.value
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`value`** از رابط {{domxref("IDBCursorWithValue")}} مقدار مکان‌نمای فعلی را برمی‌گرداند، هر مقداری که باشد.

## مقدار

مقدار مکان‌نمای فعلی.

## مثال‌ها

در این مثال، یک تراکنش می‌سازیم، یک object store دریافت می‌کنیم و سپس از یک مکان‌نما برای پیمایش همه رکوردهای موجود در object store استفاده می‌کنیم. در هر تکرار، مقدار مکان‌نما را با `cursor.value` در لاگ می‌نویسیم.

مکان‌نما نیازی ندارد که داده‌ها را بر اساس یک کلید انتخاب کنیم؛ می‌توانیم همه آن‌ها را برداریم. همچنین توجه کنید که در هر تکرار حلقه، می‌توانید داده‌های رکورد فعلی را از طریق شیء مکان‌نما با استفاده از `cursor.value.foo` دریافت کنید.
برای مشاهده یک مثال کامل و قابل اجرا، به [نمونه IDBCursor](https://github.com/mdn/dom-examples/tree/main/indexeddb-examples/idbcursor) مراجعه کنید ([مشاهده مثال آنلاین](https://mdn.github.io/dom-examples/indexeddb-examples/idbcursor/).)

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

      console.log(cursor.value);
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
- دریافت و ایجاد تغییرات در داده‌هایتان: {{domxref("IDBObjectStore")}}
- استفاده از مکان‌نماها: {{domxref("IDBCursor")}}
- نمونه مرجع: [اعلان‌های کارها](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال آنلاین](https://mdn.github.io/dom-examples/to-do-notifications/)).
---
title: "IDBCursor: source property"
short-title: source
slug: Web/API/IDBCursor/source
page-type: web-api-instance-property
browser-compat: api.IDBCursor.source
---

{{APIRef("IndexedDB")}} {{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`source`** در رابط {{domxref("IDBCursor")}}، شیء {{domxref("IDBObjectStore")}} یا {{domxref("IDBIndex")}}‌ای را برمی‌گرداند که مکان‌نما روی آن در حال پیمایش است. این ویژگی هرگز `null` برنمی‌گرداند و استثنا پرتاب نمی‌کند؛ حتی اگر مکان‌نما در حال حاضر در حال پیمایش باشد، از انتها عبور کرده باشد، یا تراکنش آن فعال نباشد.

## مقدار

شیء {{domxref("IDBObjectStore")}} یا {{domxref("IDBIndex")}} که مکان‌نما در حال پیمایش روی آن است.

## مثال‌ها

در این بخش ساده، یک تراکنش می‌سازیم، یک object store دریافت می‌کنیم و سپس با استفاده از یک مکان‌نما، تمام رکوردهای موجود در object store را پیمایش می‌کنیم. در هر تکرار، منبع مکان‌نما را ثبت (log) می‌کنیم که شیء {{domxref("IDBObjectStore")}} ما را در کنسول ثبت می‌کند.

مکان‌نما الزامی ندارد که داده‌ها را بر اساس یک کلید انتخاب کنیم؛ می‌توانیم به‌سادگی همه آن‌ها را دریافت کنیم. همچنین توجه داشته باشید که در هر تکرار حلقه، می‌توانید داده‌های رکورد جاری را از طریق شیء مکان‌نما و با استفاده از `cursor.value.foo` دریافت کنید. برای یک مثال کامل و قابل اجرا، به [نمونه IDBCursor](https://github.com/mdn/dom-examples/tree/main/indexeddb-examples/idbcursor) مراجعه کنید ([مشاهده مثال به‌صورت زنده](https://mdn.github.io/dom-examples/indexeddb-examples/idbcursor/)).

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

      console.log(cursor.source);
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

## جستارهای وابسته

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم محدوده کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌هایتان: {{domxref("IDBObjectStore")}}
- استفاده از مکان‌نماها: {{domxref("IDBCursor")}}
- نمونه مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال به‌صورت زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
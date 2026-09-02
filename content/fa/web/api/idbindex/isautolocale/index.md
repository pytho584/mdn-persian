---
title: "IDBIndex: isAutoLocale property"
short-title: isAutoLocale
slug: Web/API/IDBIndex/isAutoLocale
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.IDBIndex.isAutoLocale
---

{{APIRef("IndexedDB")}}{{deprecated_header}}{{non-standard_header}}

خاصیت فقط-خواندنی **`isAutoLocale`** از رابط {{domxref("IDBIndex")}} یک مقدار بولی (Boolean) برمی‌گرداند که نشان می‌دهد آیا ایندکس هنگام ایجاد خود مقدار `locale` را برابر `auto` داشته است یا خیر (به پارامتر [`options`](/en-US/docs/Web/API/IDBObjectStore/createIndex#options) در [`IDBObjectStore.createIndex()`](/en-US/docs/Web/API/IDBObjectStore/createIndex) مراجعه کنید).

## مقدار

یک مقدار بولی.

## مثال‌ها

در مثال زیر، یک تراکنش (transaction) و یک فروشگاه شیء (object store) باز می‌کنیم، سپس ایندکس `lName` را از یک پایگاه داده ساده مخاطبین دریافت می‌کنیم. سپس با استفاده از {{domxref("IDBIndex.openCursor")}} یک مکان‌نما (cursor) پایه روی ایندکس باز می‌کنیم — این کار مشابه باز کردن مستقیم یک مکان‌نما روی یک `ObjectStore` با استفاده از {{domxref("IDBObjectStore.openCursor")}} است، با این تفاوت که رکوردهای برگشتی بر اساس ایندکس مرتب می‌شوند، نه بر اساس کلید اصلی.

مقدار `isAutoLocale` در کنسول ثبت می‌شود.

```js
function displayDataByIndex() {
  tableEntry.textContent = "";
  const transaction = db.transaction(["contactsList"], "readonly");
  const objectStore = transaction.objectStore("contactsList");

  const myIndex = objectStore.index("lName");
  console.log(myIndex.isAutoLocale);

  myIndex.openCursor().onsuccess = (event) => {
    const cursor = event.target.result;
    if (cursor) {
      const tableRow = document.createElement("tr");
      for (const cell of [
        cursor.value.id,
        cursor.value.lName,
        cursor.value.fName,
        cursor.value.jTitle,
        cursor.value.company,
        cursor.value.eMail,
        cursor.value.phone,
        cursor.value.age,
      ]) {
        const tableCell = document.createElement("td");
        tableCell.textContent = cell;
        tableRow.appendChild(tableCell);
      }
      tableEntry.appendChild(tableRow);

      cursor.continue();
    } else {
      console.log("Entries all displayed.");
    }
  };
}
```

## مشخصات

در حال حاضر بخشی از هیچ مشخصاتی نیست.

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم یک بازه از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌های خود: {{domxref("IDBObjectStore")}}
- استفاده از مکان‌نماها: {{domxref("IDBCursor")}}
- نمونه مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
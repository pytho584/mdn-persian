---
title: "IDBIndex: locale property"
short-title: locale
slug: Web/API/IDBIndex/locale
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.IDBIndex.locale
---

{{APIRef("IndexedDB")}}{{deprecated_header}}{{non-standard_header}}

ویژگی **`locale`** (فقط‌خواندنی) در رابط {{domxref("IDBIndex")}}، locale ایندکس را برمی‌گرداند (برای مثال `en-US` یا `pl`) اگر هنگام ایجاد ایندکس مقدار `locale` برای آن تعیین شده باشد (به پارامتر [`options`](/en-US/docs/Web/API/IDBObjectStore/createIndex#options) در [`IDBObjectStore.createIndex()`](/en-US/docs/Web/API/IDBObjectStore/createIndex) مراجعه کنید). توجه کنید که این ویژگی همیشه locale جاریِ استفاده‌شده در این ایندکس را برمی‌گرداند؛ به عبارت دیگر، هرگز `"auto"` را برنمی‌گرداند.

## مقدار

یک رشته.

## مثال‌ها

در مثال زیر، یک تراکنش و یک object store باز می‌کنیم و سپس ایندکس `lName` را از یک پایگاه‌داده‌ی ساده‌ی مخاطبان می‌گیریم. سپس با استفاده از {{domxref("IDBIndex.openCursor")}} یک cursor پایه روی ایندکس باز می‌کنیم — این کار دقیقاً مانند باز کردن cursor به‌طور مستقیم روی یک `ObjectStore` با استفاده از {{domxref("IDBObjectStore.openCursor")}} عمل می‌کند، با این تفاوت که رکوردهای برگشتی بر اساس ایندکس مرتب می‌شوند، نه بر اساس کلید اصلی.

مقدار `locale` در کنسول ثبت می‌شود.

```js
function displayDataByIndex() {
  tableEntry.textContent = "";
  const transaction = db.transaction(["contactsList"], "readonly");
  const objectStore = transaction.objectStore("contactsList");

  const myIndex = objectStore.index("lName");
  console.log(myIndex.locale);

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

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم محدوده‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌های خود: {{domxref("IDBObjectStore")}}
- استفاده از cursorها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده‌ی مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
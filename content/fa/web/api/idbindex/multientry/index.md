---
title: "IDBIndex: multiEntry property"
short-title: multiEntry
slug: Web/API/IDBIndex/multiEntry
page-type: web-api-instance-property
browser-compat: api.IDBIndex.multiEntry
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`multiEntry`** از رابط {{domxref("IDBIndex")}} یک مقدار بولی برمی‌گرداند که بر رفتار ایندکس اثر می‌گذارد وقتی نتیجهٔ ارزیابی مسیر کلید ایندکس به یک آرایه منجر شود.

این رفتار هنگام ایجاد ایندکس و با استفاده از متد {{domxref("IDBObjectStore.createIndex")}} تعیین می‌شود. این متد یک پارامتر اختیاری به نام `options` می‌پذیرد که ویژگی `multiEntry` آن روی `true`/`false` تنظیم می‌شود.

## مقدار

| مقدار | اثر |
| ----- | ------------------------------------------------------------------- |
| true  | به ازای هر آیتم در یک آرایه از کلیدها، یک رکورد در ایندکس وجود دارد. |
| false | به ازای هر کلید که یک آرایه است، یک رکورد وجود دارد.                  |

## مثال‌ها

در مثال زیر، یک تراکنش و یک object store باز می‌کنیم و سپس ایندکس `lName` را از یک پایگاه‌دادهٔ سادهٔ مخاطبان به دست می‌آوریم. سپس با استفاده از {{domxref("IDBIndex.openCursor")}} یک cursor پایه روی ایندکس باز می‌کنیم — این کار همانند باز کردن مستقیم cursor روی `ObjectStore` با استفاده از {{domxref("IDBObjectStore.openCursor")}} است، با این تفاوت که رکوردهای بازگشتی بر اساس ایندکس مرتب می‌شوند، نه بر اساس کلید اصلی.

وضعیت multi-entry ایندکس در کنسول ثبت می‌شود: باید به‌صورت `false` برگردانده شود.

در پایان، روی هر رکورد پیمایش می‌کنیم و داده‌ها را در یک جدول HTML قرار می‌دهیم. برای مشاهدهٔ یک مثال کامل و قابل اجرا، به [مخزن دموی IndexedDB-examples](https://github.com/mdn/dom-examples/tree/main/indexeddb-examples/idbindex) مراجعه کنید ([مشاهدهٔ مثال به‌صورت زنده](https://mdn.github.io/dom-examples/indexeddb-examples/idbindex/)).

```js
function displayDataByIndex() {
  tableEntry.textContent = "";
  const transaction = db.transaction(["contactsList"], "readonly");
  const objectStore = transaction.objectStore("contactsList");

  const myIndex = objectStore.index("lName");
  console.log(myIndex.multiEntry);

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

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم محدوده‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و اعمال تغییرات روی داده‌ها: {{domxref("IDBObjectStore")}}
- استفاده از cursorها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهدهٔ مثال به‌صورت زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
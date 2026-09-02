---
title: "IDBIndex: objectStore property"
short-title: objectStore
slug: Web/API/IDBIndex/objectStore
page-type: web-api-instance-property
browser-compat: api.IDBIndex.objectStore
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

ویژگی **`objectStore`** از رابط {{domxref("IDBIndex")}}، فروشگاه شیء (object store) ارجاع‌داده‌شده توسط ایندکس فعلی را بازمی‌گرداند.

## مقدار

یک {{domxref("IDBObjectStore")}}.

## مثال‌ها

در مثال زیر، یک تراکنش و یک فروشگاه شیء باز می‌کنیم، سپس ایندکس `lName` را از یک پایگاه داده ساده مخاطبین دریافت می‌کنیم. سپس با استفاده از {{domxref("IDBIndex.openCursor")}} یک مکان‌نما (cursor) پایه روی ایندکس باز می‌کنیم. این کار همانند باز کردن مستقیم یک مکان‌نما روی یک `ObjectStore` با استفاده از {{domxref("IDBObjectStore.openCursor")}} عمل می‌کند، با این تفاوت که رکوردهای بازگشتی بر اساس ایندکس مرتب می‌شوند، نه بر اساس کلید اصلی.

فروشگاه شیء جاری در کنسول ثبت می‌شود: باید چیزی شبیه به این بازگردانده شود:

```plain
IDBObjectStore { name: "contactsList", keyPath: "id", indexNames: DOMStringList[7], transaction: IDBTransaction, autoIncrement: false }
```

در نهایت، در هر رکورد پیمایش می‌کنیم و داده‌ها را در یک جدول HTML درج می‌کنیم. برای یک مثال کامل و عملی، به [مخزن دموی IndexedDB-examples](https://github.com/mdn/dom-examples/tree/main/indexeddb-examples/idbindex) مراجعه کنید ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/indexeddb-examples/idbindex/)).

```js
function displayDataByIndex() {
  tableEntry.textContent = "";
  const transaction = db.transaction(["contactsList"], "readonly");
  const objectStore = transaction.objectStore("contactsList");

  const myIndex = objectStore.index("lName");
  console.log(myIndex.objectStore);

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
- تنظیم یک بازه از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌های خود: {{domxref("IDBObjectStore")}}
- استفاده از مکان‌نماها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
```yaml
---
title: "IDBIndex: keyPath property"
short-title: keyPath
slug: Web/API/IDBIndex/keyPath
page-type: web-api-instance-property
browser-compat: api.IDBIndex.keyPath
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

ویژگی **`keyPath`** از رابط {{domxref("IDBIndex")}}، [مسیر کلید (key path)](/en-US/docs/Web/API/IndexedDB_API/Basic_Terminology#key_path) ایندکس جاری را برمی‌گرداند. اگر `null` باشد، این ایندکس به صورت خودکار پر نمی‌شود.

## مقدار

هر نوع داده‌ای که می‌تواند به عنوان مسیر کلید استفاده شود.

## مثال‌ها

در مثال زیر، یک تراکنش و یک فروشگاه شیء باز می‌کنیم و سپس ایندکس `lName` را از یک پایگاه داده ساده مخاطبین دریافت می‌کنیم. سپس یک کرسر پایه روی ایندکس با استفاده از {{domxref("IDBIndex.openCursor")}} باز می‌کنیم — این کار مشابه باز کردن مستقیم یک کرسر روی یک `ObjectStore` با {{domxref("IDBObjectStore.openCursor")}} است، با این تفاوت که رکوردهای برگشتی بر اساس ایندکس مرتب شده‌اند، نه کلید اصلی.

مسیر کلید ایندکس جاری در کنسول ثبت می‌شود: باید به صورت `lName` برگردانده شود.

در نهایت، روی هر رکورد پیمایش می‌کنیم و داده‌ها را در یک جدول HTML درج می‌کنیم. برای یک مثال کامل و قابل اجرا، به مخزن دموی [IndexedDB-examples](https://github.com/mdn/dom-examples/tree/main/indexeddb-examples/idbindex) مراجعه کنید ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/indexeddb-examples/idbindex/)).

```js
function displayDataByIndex() {
  tableEntry.textContent = "";
  const transaction = db.transaction(["contactsList"], "readonly");
  const objectStore = transaction.objectStore("contactsList");

  const myIndex = objectStore.index("lName");
  console.log(myIndex.keyPath);

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

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم یک بازه از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌های خود: {{domxref("IDBObjectStore")}}
- استفاده از کرسرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
```
---
title: "IDBIndex: unique property"
short-title: unique
slug: Web/API/IDBIndex/unique
page-type: web-api-instance-property
browser-compat: api.IDBIndex.unique
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

ویژگی فقطخواندنی **`unique`** یک مقدار بولی (boolean) برمی‌گرداند که مشخص می‌کند آیا ایندکس امکان کلیدهای تکراری را می‌دهد یا خیر.

این موضوع هنگام ایجاد ایندکس و با استفاده از متد {{domxref("IDBObjectStore.createIndex")}} تعیین می‌شود. این متد یک پارامتر اختیاری به نام `unique` دریافت می‌کند که اگر روی `true` تنظیم شود، به این معنی است که ایندکس نمی‌تواند ورودی‌های تکراری را بپذیرد.

## مقدار

یک مقدار بولی:

| مقدار   | تأثیر                                                    |
| ------- | -------------------------------------------------------- |
| `true`  | ایندکس فعلی مقادیر تکراری را برای یک کلید مجاز نمی‌داند. |
| `false` | ایندکس فعلی مقادیر کلید تکراری را مجاز می‌داند.          |

## مثال‌ها

در مثال زیر، یک تراکنش و یک object store باز می‌کنیم، سپس ایندکس `lName` را از یک پایگاه داده ساده مخاطبین دریافت می‌کنیم. سپس یک کرسر پایه روی ایندکس با استفاده از {{domxref("IDBIndex.openCursor")}} باز می‌کنیم — این کار مشابه باز کردن مستقیم یک کرسر روی `ObjectStore` با استفاده از {{domxref("IDBObjectStore.openCursor")}} است، با این تفاوت که رکوردهای برگشتی بر اساس ایندکس مرتب شده‌اند، نه بر اساس کلید اصلی.

وضعیت یکتایی (unique) ایندکس در کنسول ثبت می‌شود: باید به صورت `false` برگردانده شود.

در نهایت، از میان هر رکورد عبور می‌کنیم و داده‌ها را در یک جدول HTML وارد می‌کنیم. برای یک مثال کامل و قابل اجرا، به مخزن دموی [IndexedDB-examples](https://github.com/mdn/dom-examples/tree/main/indexeddb-examples/idbindex) مراجعه کنید ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/indexeddb-examples/idbindex/)).

```js
function displayDataByIndex() {
  tableEntry.textContent = "";
  const transaction = db.transaction(["contactsList"], "readonly");
  const objectStore = transaction.objectStore("contactsList");

  const myIndex = objectStore.index("lName");
  console.log(myIndex.unique);

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
- استفاده از کرسرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
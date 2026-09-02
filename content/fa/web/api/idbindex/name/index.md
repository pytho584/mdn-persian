---
title: "IDBIndex: name property"
short-title: name
slug: Web/API/IDBIndex/name
page-type: web-api-instance-property
browser-compat: api.IDBIndex.name
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

ویژگی **`name`** از رابط {{domxref("IDBIndex")}} یک رشته را شامل می‌شود که نام ایندکس را مشخص می‌کند.

## مقدار

یک رشته که نام ایندکس را مشخص می‌کند.

### استثناها

چندین استثنا وجود دارد که می‌توانند هنگام تلاش برای تغییر نام یک ایندکس رخ دهند.

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر ایندکس یا ذخیره‌گاه شیء (object store) آن حذف شده باشد، یا اگر تراکنش جاری یک تراکنش ارتقاء (upgrade transaction) نباشد، پرتاب می‌شود. شما فقط می‌توانید در طول تراکنش‌های ارتقاء ایندکس‌ها را تغییر نام دهید؛ یعنی زمانی که حالت (mode) `"versionchange"` است.
- `TransactionInactiveError` {{domxref("DOMException")}}
  - : اگر تراکنش جاری فعال نباشد، پرتاب می‌شود.
- `ConstraintError` {{domxref("DOMException")}}
  - : اگر یک ایندکس دیگر از قبل از نام مشخص‌شده استفاده کند، پرتاب می‌شود.

## مثال‌ها

در مثال زیر، یک تراکنش و یک ذخیره‌گاه شیء باز می‌کنیم، سپس ایندکس `lName` را از یک پایگاه داده ساده مخاطبین دریافت می‌کنیم. سپس یک مکان‌نمای (cursor) پایه روی ایندکس با استفاده از {{domxref("IDBIndex.openCursor()")}} باز می‌کنیم — این کار مشابه باز کردن مستقیم یک مکان‌نما روی یک {{domxref("IDBObjectStore")}} با استفاده از {{domxref("IDBObjectStore.openCursor", "openCursor()")}} است، با این تفاوت که رکوردهای بازگشتی بر اساس ایندکس مرتب شده‌اند، نه کلید اصلی.

نام ایندکس در کنسول ثبت می‌شود: باید به صورت `lName` بازگردانده شود.

در نهایت، از میان هر رکورد عبور می‌کنیم و داده‌ها را در یک جدول HTML وارد می‌کنیم. برای یک مثال کامل و کارآمد، به [مخزن دموی IndexedDB-examples](https://github.com/mdn/dom-examples/tree/main/indexeddb-examples/idbindex) مراجعه کنید ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/indexeddb-examples/idbindex/)).

```js
function displayDataByIndex() {
  tableEntry.textContent = "";
  const transaction = db.transaction(["contactsList"], "readonly");
  const objectStore = transaction.objectStore("contactsList");

  const myIndex = objectStore.index("lName");
  console.log(myIndex.name);

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
- تنظیم محدوده کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌هایتان: {{domxref("IDBObjectStore")}}
- استفاده از مکان‌نماها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
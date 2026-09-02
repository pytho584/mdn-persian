---
title: "IDBIndex: openCursor() method"
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

متد **`openCursor()`** از رابط {{domxref("IDBIndex")}} یک شی {{domxref("IDBRequest")}} برمی‌گرداند و در یک نخ جداگانه، یک مکان‌نما (cursor) روی محدوده کلید مشخص‌شده ایجاد می‌کند.

این متد موقعیت مکان‌نما را بر اساس جهت مشخص‌شده، به رکورد مناسب تنظیم می‌کند.

اگر محدوده کلید مشخص نشده یا `null` باشد، محدوده شامل تمام رکوردها خواهد بود.

## نحو (Syntax)

```js-nolint
openCursor()
openCursor(range)
openCursor(range, direction)
```

### پارامترها

- `range` {{optional_inline}}
  - : یک کلید یا {{domxref("IDBKeyRange")}} برای استفاده به عنوان محدوده مکان‌نما. اگر چیزی ارسال نشود، به طور پیش‌فرض به یک محدوده کلید که تمام رکوردهای این ذخیره‌گاه شیء را انتخاب می‌کند، تنظیم می‌شود.
- `direction` {{optional_inline}}
  - : جهت مکان‌نما. برای مقادیر ممکن به [ثابت‌های IDBCursor](/en-US/docs/Web/API/IDBCursor#constants) مراجعه کنید.

### مقدار بازگشتی

یک شی {{domxref("IDBRequest")}} که رویدادهای مربوط به این عملیات روی آن رخ می‌دهد.

اگر عملیات موفق باشد، مقدار ویژگی {{domxref("IDBRequest.result", "result")}} درخواست به صورت زیر است:

- یک شی {{domxref("IDBCursorWithValue")}} که به اولین رکورد مطابق با پرس‌وجوی داده شده اشاره می‌کند
- اگر هیچ رکورد منطبقی یافت نشود، `null`

### استثناها

این متد ممکن است یک {{domxref("DOMException")}} از یکی از انواع زیر ایجاد کند:

- `TransactionInactiveError` {{domxref("DOMException")}}
  - : اگر تراکنش این {{domxref("IDBIndex")}} غیرفعال باشد.
- {{jsxref("TypeError")}}
  - : اگر مقدار پارامتر `direction` نامعتبر باشد.
- `DataError` {{domxref("DOMException")}}
  - : اگر کلید یا محدوده کلید ارائه‌شده حاوی یک کلید نامعتبر باشد.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر {{domxref("IDBIndex")}} حذف یا پاک شده باشد.

## مثال‌ها

در مثال زیر، ما یک تراکنش و یک ذخیره‌گاه شیء باز می‌کنیم، سپس ایندکس `lName` را از یک پایگاه داده ساده مخاطبین دریافت می‌کنیم. سپس یک مکان‌نمای پایه روی ایندکس با استفاده از `openCursor()` باز می‌کنیم — این کار مشابه باز کردن مستقیم یک مکان‌نما روی یک `ObjectStore` با استفاده از {{domxref("IDBObjectStore.openCursor")}} است، با این تفاوت که رکوردهای برگشتی بر اساس ایندکس مرتب شده‌اند، نه کلید اصلی.

در نهایت، از میان هر رکورد تکرار می‌کنیم و داده‌ها را در یک جدول HTML وارد می‌کنیم. برای یک مثال کامل و در حال اجرا، به [مخزن دموی IndexedDB-examples](https://github.com/mdn/dom-examples/tree/main/indexeddb-examples/idbindex) ما مراجعه کنید ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/indexeddb-examples/idbindex/)).

```js
function displayDataByIndex() {
  tableEntry.textContent = "";
  const transaction = db.transaction(["contactsList"], "readonly");
  const objectStore = transaction.objectStore("contactsList");

  const myIndex = objectStore.index("lName");

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
- بازیابی و ایجاد تغییرات در داده‌ها: {{domxref("IDBObjectStore")}}
- استفاده از مکان‌نماها: {{domxref("IDBCursor")}}
- مثال مرجع: [اعلان‌های کارهای روزانه (To-do Notifications)](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/))
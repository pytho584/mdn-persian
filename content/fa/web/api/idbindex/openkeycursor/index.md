---
title: "IDBIndex: openKeyCursor() method"
short-title: openKeyCursor()
slug: Web/API/IDBIndex/openKeyCursor
page-type: web-api-instance-method
browser-compat: api.IDBIndex.openKeyCursor
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

متد **`openKeyCursor()`** در رابط {{domxref("IDBIndex")}} یک شیء {{domxref("IDBRequest")}} برمی‌گرداند و در یک نخ جداگانه، یک نشانگر (cursor) روی بازه‌ی کلید مشخص‌شده ایجاد می‌کند که بر اساس این ایندکس مرتب شده است.

این متد موقعیت نشانگر را بر اساس جهت مشخص‌شده، روی کلید مناسب قرار می‌دهد.

اگر بازه‌ی کلید مشخص نشده باشد یا `null` باشد، بازه شامل همه‌ی کلیدها خواهد بود.

> [!NOTE]
> نشانگرهایی که توسط `openKeyCursor()` برگردانده می‌شوند، مقدار ارجاع‌داده‌شده را مانند [`IDBIndex.openCursor`](/en-US/docs/Web/API/IDBIndex/openCursor) در دسترس قرار نمی‌دهند. این کار دریافت فهرست کلیدها را بسیار کارآمدتر می‌کند.

## Syntax

```js-nolint
openKeyCursor()
openKeyCursor(range)
openKeyCursor(range, direction)
```

### Parameters

- `range` {{optional_inline}}
  - : یک کلید یا {{domxref("IDBKeyRange")}} که به عنوان بازه‌ی نشانگر استفاده می‌شود. اگر چیزی ارسال نشود، به‌طور پیش‌فرض به یک بازه‌ی کلیدی تبدیل می‌شود که همه‌ی رکوردهای این object store را انتخاب می‌کند.
- `direction` {{optional_inline}}
  - : [جهت](/en-US/docs/Web/API/IDBCursor#constants) نشانگر. برای مقادیر ممکن به [ثابت‌های IDBCursor](/en-US/docs/Web/API/IDBCursor#constants) مراجعه کنید.

### Return value

یک شیء {{domxref("IDBRequest")}} که رویدادهای بعدی مرتبط با این عملیات روی آن ارسال می‌شوند.

اگر عملیات موفق باشد، مقدار ویژگی {{domxref("IDBRequest.result", "result")}} درخواست عبارت است از:

- یک شیء {{domxref("IDBCursor")}} که به اولین رکورد منطبق با پرس‌وجوی داده‌شده اشاره می‌کند
- در صورت نبود هیچ رکورد منطبقی، مقدار `null`

### Exceptions

این متد ممکن است یک {{domxref("DOMException")}} از یکی از انواع زیر صادر کند:

- `TransactionInactiveError` {{domxref("DOMException")}}
  - : اگر تراکنش این {{domxref("IDBIndex")}} غیرفعال باشد پرتاب می‌شود.
- {{jsxref("TypeError")}}
  - : اگر مقدار پارامتر جهت نامعتبر باشد پرتاب می‌شود.
- `DataError` {{domxref("DOMException")}}
  - : اگر کلید یا بازه‌ی کلیدی ارائه‌شده حاوی یک کلید نامعتبر باشد پرتاب می‌شود.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر {{domxref("IDBIndex")}} حذف شده باشد یا دیگر وجود نداشته باشد پرتاب می‌شود.

## Examples

در مثال زیر، یک تراکنش و یک object store باز می‌کنیم و سپس ایندکس `lName` را از یک پایگاه‌داده‌ی ساده‌ی مخاطبین دریافت می‌کنیم. سپس با استفاده از `openKeyCursor()` یک نشانگر کلید روی ایندکس باز می‌کنیم — این کار مانند باز کردن مستقیم نشانگر روی یک `ObjectStore` با استفاده از {{domxref("IDBObjectStore.openKeyCursor")}} عمل می‌کند، با این تفاوت که رکوردهای برگشتی بر اساس ایندکس مرتب می‌شوند، نه بر اساس کلید اصلی.

در پایان، از میان هر رکورد در ایندکس عبور می‌کنیم و نام خانوادگی و کلید اصلی متناظر با رکورد ارجاع‌داده‌شده را در یک جدول HTML وارد می‌کنیم.

```js
function displayDataByIndex() {
  tableEntry.textContent = "";
  const transaction = db.transaction(["contactsList"], "readonly");
  const objectStore = transaction.objectStore("contactsList");

  const myIndex = objectStore.index("lName");

  myIndex.openKeyCursor().onsuccess = (event) => {
    const cursor = event.target.result;
    if (cursor) {
      const tableRow = document.createElement("tr");
      tableRow.appendChild(document.createElement("td")).textContent =
        cursor.key;
      tableRow.appendChild(document.createElement("td")).textContent =
        cursor.primaryKey;
      tableEntry.appendChild(tableRow);

      cursor.continue();
    } else {
      console.log("All last names displayed.");
    }
  };
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم بازه‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- دریافت و تغییر داده‌ها: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده‌ی مثال به‌صورت زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
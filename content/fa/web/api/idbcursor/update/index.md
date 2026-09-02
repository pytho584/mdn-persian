---
title: "IDBCursor: update() method"
short-title: update()
slug: Web/API/IDBCursor/update
page-type: web-api-instance-method
browser-compat: api.IDBCursor.update
---

{{APIRef("IndexedDB")}} {{AvailableInWorkers}}

متد **`update()`** در رابط {{domxref("IDBCursor")}} یک شیء {{domxref("IDBRequest")}} برمی‌گرداند و در یک ریسهٔ جداگانه، مقدار را در موقعیت فعلی نشانگر در object store به‌روزرسانی می‌کند. اگر نشانگر به رکوردی اشاره کند که به‌تازگی حذف شده است، یک رکورد جدید ایجاد می‌شود.

توجه داشته باشید که نمی‌توانید `update()` (یا {{domxref("IDBCursor.delete()")}}) را روی نشانگرهایی که از {{domxref("IDBIndex.openKeyCursor()")}} دریافت شده‌اند فراخوانی کنید. برای چنین نیازهایی، باید به‌جای آن از {{domxref("IDBIndex.openCursor()")}} استفاده کنید.

## نحو

```js-nolint
update(value)
```

### پارامترها

- `value`
  - : مقدار جدیدی که در موقعیت فعلی ذخیره می‌شود.

### مقدار بازگشتی

یک شیء {{domxref("IDBRequest")}} که رویدادهای بعدی مرتبط با این عملیات روی آن ارسال می‌شوند.

اگر عملیات موفق باشد، مقدار خصوصیت {{domxref("IDBRequest.result", "result")}} درخواست، کلید رکورد به‌روزرسانی‌شده است.

### استثناها

این متد ممکن است یک {{domxref("DOMException")}} از یکی از انواع زیر ایجاد کند:

- `TransactionInactiveError` {{domxref("DOMException")}}
  - : اگر تراکنش این `IDBCursor` غیرفعال باشد، پرتاب می‌شود.
- `ReadOnlyError` {{domxref("DOMException")}}
  - : اگر حالت تراکنش فقط‌خواندنی باشد، پرتاب می‌شود.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر نشانگر با استفاده از {{domxref("IDBindex.openKeyCursor")}} ساخته شده باشد، در حال حاضر در حال تکرار باشد، یا از انتهای خود گذشته باشد، پرتاب می‌شود.
- `DataError` {{domxref("DOMException")}}
  - : اگر object store زیرین از کلیدهای درون‌خطی استفاده کند و ویژگیِ موجود در مقدارِ مسیر کلیدِ object store با کلیدِ موقعیت این نشانگر مطابقت نداشته باشد، پرتاب می‌شود.
- `DataCloneError` {{domxref("DOMException")}}
  - : اگر داده‌های در حال ذخیره‌سازی نتوانند توسط الگوریتم کلون‌سازی ساختاریافتهٔ داخلی کلون شوند، پرتاب می‌شود.

## مثال‌ها

در این قطعهٔ ساده، یک تراکنش ایجاد می‌کنیم، یک object store دریافت می‌کنیم و سپس با استفاده از یک نشانگر، همهٔ رکوردهای object store را پیمایش می‌کنیم. اگر `albumTitle` نشانگر فعلی برابر با «A farewell to kings» باشد، سال انتشار آلبوم را با استفاده از `const request = cursor.update();` به‌روزرسانی می‌کنیم.

توجه داشته باشید که نمی‌توانید کلیدهای اصلی را با استفاده از `cursor.update()` تغییر دهید؛ به همین دلیل عنوان آلبوم را تغییر نمی‌دهیم؛ زیرا این کار یکپارچگی داده را از بین می‌برد. در چنین شرایطی، باید کل رکورد را حذف و سپس با استفاده از {{domxref("IDBObjectStore.add")}} رکورد جدیدی اضافه کنید. همچنین توجه کنید که نمی‌توانید مستقیماً `cursor.value` را در فراخوانی `update` قرار دهید؛ به همین دلیل مثال زیر از متغیر واسط `updateData` استفاده می‌کند.

نشانگر لازم ندارد که داده‌ها را بر اساس یک کلید انتخاب کنیم؛ می‌توانیم به‌سادگی همهٔ آن‌ها را برداریم. همچنین در هر تکرار حلقه، می‌توانید داده‌های رکورد فعلی را از طریق شیء نشانگر با استفاده از `cursor.value.foo` دریافت کنید. برای یک مثال کامل و کاری، به [IDBCursor example](https://github.com/mdn/dom-examples/tree/main/indexeddb-examples/idbcursor) مراجعه کنید ([مشاهدهٔ مثال زنده](https://mdn.github.io/dom-examples/indexeddb-examples/idbcursor/)).

```js
function updateResult() {
  list.textContent = "";
  const transaction = db.transaction(["rushAlbumList"], "readwrite");
  const objectStore = transaction.objectStore("rushAlbumList");

  objectStore.openCursor().onsuccess = (event) => {
    const cursor = event.target.result;
    if (cursor) {
      if (cursor.value.albumTitle === "A farewell to kings") {
        const updateData = cursor.value;

        updateData.year = 2050;
        const request = cursor.update(updateData);
        request.onsuccess = () => {
          console.log("A better album year?");
        };
      }

      const listItem = document.createElement("li");
      listItem.textContent = `${cursor.value.albumTitle}, ${cursor.value.year}`;
      list.appendChild(listItem);
      cursor.continue();
    } else {
      console.log("Entries displayed.");
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
- تنظیم بازه‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌های خود: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهدهٔ مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
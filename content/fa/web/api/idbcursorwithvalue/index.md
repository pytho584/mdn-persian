---
title: IDBCursorWithValue
slug: Web/API/IDBCursorWithValue
page-type: web-api-interface
browser-compat: api.IDBCursorWithValue
---

{{APIRef("IndexedDB")}} {{AvailableInWorkers}}

رابط **`IDBCursorWithValue`** در [IndexedDB API](/en-US/docs/Web/API/IndexedDB_API) یک [نشانگر (cursor)](/en-US/docs/Web/API/IndexedDB_API/Basic_Terminology#cursor) برای پیمایش یا تکرار روی چندین رکورد در پایگاه‌داده است. این رابط همان {{domxref("IDBCursor")}} است، با این تفاوت که ویژگی `value` را نیز شامل می‌شود.

نشانگر دارای یک منبع است که مشخص می‌کند روی کدام ایندکس یا object store (ذخیره‌گاه شیء) در حال تکرار است. نشانگر موقعیتی در محدوده (range) دارد و در جهتی حرکت می‌کند که به ترتیب کلیدهای رکورد، صعودی یا نزولی است. نشانگر به برنامه اجازه می‌دهد تا همه رکوردهای درون محدودهٔ نشانگر را به‌صورت ناهمگام (asynchronous) پردازش کند.

می‌توانید به‌طور هم‌زمان تعداد نامحدودی نشانگر داشته باشید. برای یک نشانگر مشخص، همیشه همان شیء `IDBCursorWithValue` را دریافت می‌کنید. عملیات روی ایندکس یا object store زیرین انجام می‌شود.

{{InheritanceDiagram}}

## متدهای نمونه

متدها را از رابط والد خود، {{domxref("IDBCursor")}} به ارث می‌برد.

## ویژگی‌های نمونه

ویژگی‌ها را از رابط والد خود، {{domxref("IDBCursor")}} به ارث می‌برد.

- {{domxref("IDBCursorWithValue.value")}} {{ReadOnlyInline}}
  - : مقدار نشانگر فعلی را بازمی‌گرداند.

## مثال

در این مثال، یک تراکنش می‌سازیم، یک object store را بازیابی می‌کنیم و سپس با استفاده از یک نشانگر، همه رکوردهای موجود در آن object store را پیمایش می‌کنیم. نشانگر نیازی ندارد که داده‌ها را بر اساس کلید انتخاب کنیم؛ می‌توانیم همه آن‌ها را دریافت کنیم. همچنین توجه داشته باشید که در هر تکرار حلقه، می‌توانید داده‌های رکورد جاری را با استفاده از `cursor.value.foo` از شیء نشانگر دریافت کنید. برای یک مثال کامل و قابل اجرا، [مثال IDBCursor](https://github.com/mdn/dom-examples/tree/main/indexeddb-examples/idbcursor) را ببینید ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/indexeddb-examples/idbcursor/).)

```js
function displayData() {
  const transaction = db.transaction(["rushAlbumList"], "readonly");
  const objectStore = transaction.objectStore("rushAlbumList");

  objectStore.openCursor().onsuccess = (event) => {
    const cursor = event.target.result;
    if (cursor) {
      const listItem = document.createElement("li");
      listItem.textContent = `${cursor.value.albumTitle}, ${cursor.value.year}`;
      list.appendChild(listItem);

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
- تنظیم محدوده‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌ها: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
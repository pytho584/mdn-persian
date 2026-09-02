---
title: "IDBCursor"
---

---
title: IDBCursor
slug: Web/API/IDBCursor
page-type: web-api-interface
browser-compat: api.IDBCursor
---

{{APIRef("IndexedDB")}} {{AvailableInWorkers}}

> [!NOTE]
> نباید با {{domxref("IDBCursorWithValue")}} اشتباه گرفته شود؛ این رابط، همان رابط **`IDBCursor`** با یک ویژگی **`value`** اضافی است.

رابط **`IDBCursor`** در [IndexedDB API](/en-US/docs/Web/API/IndexedDB_API) یک [نشانگر (cursor)](/en-US/docs/Web/API/IndexedDB_API/Basic_Terminology#cursor) را برای پیمایش یا تکرار روی چندین رکورد در یک پایگاه‌داده نشان می‌دهد.

نشانگر دارای یک «منبع» (source) است که مشخص می‌کند در حال تکرار روی کدام ایندکس یا object store است. همچنین در محدوده‌ی (range) خود یک موقعیت دارد و در جهتی حرکت می‌کند که به ترتیب کلیدهای رکورد، صعودی یا نزولی است. این نشانگر به برنامه اجازه می‌دهد تا همه‌ی رکوردهای موجود در محدوده‌ی نشانگر را به‌صورت ناهمگام (asynchronous) پردازش کند.

شما می‌توانید به‌طور همزمان تعداد نامحدودی نشانگر داشته باشید. برای هر نشانگر، همیشه همان شیء `IDBCursor` یکسان را دریافت می‌کنید. عملیات روی ایندکس یا object store زیرین انجام می‌شود.

## ویژگی‌های نمونه

> [!NOTE]
> {{domxref("IDBCursorWithValue")}} یک رابط **`IDBCursor`** با یک ویژگی **`value`** اضافی است.

- {{domxref("IDBCursor.source")}} {{ReadOnlyInline}}
  - : مقدار {{domxref("IDBObjectStore")}} یا {{domxref("IDBIndex")}} را که نشانگر در حال تکرار روی آن است برمی‌گرداند. این تابع هرگز `null` برنمی‌گرداند و استثنا پرتاب نمی‌کند، حتی اگر نشانگر در حال تکرار باشد، از انتهای محدوده‌اش گذشته باشد، یا تراکنش آن فعال نباشد.
- {{domxref("IDBCursor.direction")}} {{ReadOnlyInline}}
  - : جهت پیمایش نشانگر را برمی‌گرداند.
- {{domxref("IDBCursor.key")}} {{ReadOnlyInline}}
  - : کلید رکورد را در موقعیت فعلی نشانگر برمی‌گرداند. اگر نشانگر خارج از محدوده‌ی خود باشد، این مقدار `undefined` تنظیم می‌شود. کلید نشانگر می‌تواند هر نوع داده‌ای باشد.
- {{domxref("IDBCursor.primaryKey")}} {{ReadOnlyInline}}
  - : کلید اصلی مؤثر فعلی نشانگر را برمی‌گرداند. اگر نشانگر در حال تکرار باشد یا از محدوده‌ی خود خارج شده باشد، این مقدار `undefined` تنظیم می‌شود. کلید اصلی نشانگر می‌تواند هر نوع داده‌ای باشد.
- {{domxref("IDBCursor.request")}} {{ReadOnlyInline}}
  - : {{domxref("IDBRequest")}} مورد استفاده برای به‌دست آوردن نشانگر را برمی‌گرداند.

## متدهای نمونه

- {{domxref("IDBCursor.advance()")}}
  - : تعداد دفعاتی را که نشانگر باید موقعیت خود را به جلو حرکت دهد، تنظیم می‌کند.
- {{domxref("IDBCursor.continue()")}}
  - : نشانگر را در جهت خود به موقعیت بعدی، یعنی آیتمی که کلیدش با پارامتر اختیاری `key` مطابقت دارد، پیش می‌برد.
- {{domxref("IDBCursor.continuePrimaryKey()")}}
  - : نشانگر را روی کلید ایندکس و کلید اصلی داده‌شده‌ به‌عنوان آرگومان تنظیم می‌کند.
- {{domxref("IDBCursor.delete()")}}
  - : یک شیء {{domxref("IDBRequest")}} برمی‌گرداند و در یک نخ جداگانه، رکورد را در موقعیت فعلی نشانگر حذف می‌کند، بدون اینکه موقعیت نشانگر تغییر کند. این روش می‌تواند برای حذف رکوردهای خاص استفاده شود.
- {{domxref("IDBCursor.update()")}}
  - : یک شیء {{domxref("IDBRequest")}} برمی‌گرداند و در یک نخ جداگانه، مقدار را در موقعیت فعلی نشانگر در object store به‌روزرسانی می‌کند. این روش می‌تواند برای به‌روزرسانی رکوردهای خاص استفاده شود.

## ثابت‌ها

{{Deprecated_Header}}

> [!WARNING]
> این ثابت‌ها دیگر در دسترس نیستند — در Gecko 25 حذف شده‌اند. به‌جای آن‌ها باید مستقیماً از ثابت‌های رشته‌ای استفاده کنید. ([باگ ۸۹۱۹۴۴ فایرفاکس](https://bugzil.la/891944))

- `NEXT`: `"next"` : نشانگر همه‌ی رکوردها را نشان می‌دهد، از جمله رکوردهای تکراری. از کران پایینی محدوده‌ی کلید شروع می‌شود و به سمت بالا حرکت می‌کند (به‌صورت یکنواخت صعودی در ترتیب کلیدها).
- `NEXTUNIQUE` : `"nextunique"` : نشانگر همه‌ی رکوردها را به‌جز موارد تکراری نشان می‌دهد. اگر چند رکورد با کلید یکسان وجود داشته باشد، فقط اولین رکوردی که پیمایش می‌شود بازیابی می‌شود. از کران پایینی محدوده‌ی کلید شروع می‌شود و به سمت بالا حرکت می‌کند.
- `PREV`: `"prev"` : نشانگر همه‌ی رکوردها را نشان می‌دهد، از جمله رکوردهای تکراری. از کران بالایی محدوده‌ی کلید شروع می‌شود و به سمت پایین حرکت می‌کند (به‌صورت یکنواخت نزولی در ترتیب کلیدها).
- `PREVUNIQUE`: `"prevunique"` : نشانگر همه‌ی رکوردها را به‌جز موارد تکراری نشان می‌دهد. اگر چند رکورد با کلید یکسان وجود داشته باشد، فقط اولین رکوردی که پیمایش می‌شود بازیابی می‌شود. از کران بالایی محدوده‌ی کلید شروع می‌شود و به سمت پایین حرکت می‌کند.

## مثال‌ها

در این قطعه‌ی ساده، یک تراکنش می‌سازیم، یک object store را بازیابی می‌کنیم و سپس با یک نشانگر، همه‌ی رکوردهای موجود در آن object store را پیمایش می‌کنیم. نشانگر الزام نمی‌کند که داده‌ها را بر اساس کلید انتخاب کنیم؛ می‌توانیم همه‌ی آن‌ها را برداریم. همچنین توجه کنید که در هر تکرار حلقه، می‌توانید داده‌های رکورد جاری را با استفاده از `cursor.value.foo` از روی شیء نشانگر بگیرید. برای یک مثال کامل و قابل اجرا، [مثال IDBCursor](https://github.com/mdn/dom-examples/tree/main/indexeddb-examples/idbcursor) را ببینید ([مشاهده‌ی مثال زنده](https://mdn.github.io/dom-examples/indexeddb-examples/idbcursor/).)

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
- بازیابی داده‌ها و ایجاد تغییرات در آن‌ها: {{domxref("IDBObjectStore")}}
- مثال مرجع: [اعلان‌های کارهای روزانه](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده‌ی مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
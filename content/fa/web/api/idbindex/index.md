---
title: IDBIndex
slug: Web/API/IDBIndex
page-type: web-api-interface
browser-compat: api.IDBIndex
---

{{APIRef("IndexedDB")}} {{AvailableInWorkers}}

اینترفیس `IDBIndex` از [IndexedDB API](/en-US/docs/Web/API/IndexedDB_API) دسترسی ناهمگام به یک [ایندکس](/en-US/docs/Web/API/IndexedDB_API/Basic_Terminology#index) در پایگاه‌داده فراهم می‌کند. ایندکس نوعی object store برای جست‌وجوی رکوردها در یک object store دیگر است که به آن «object store مرجع» گفته می‌شود. برای بازیابی داده‌ها از این اینترفیس استفاده می‌کنید.

می‌توانید رکوردها را در یک object store یا از طریق کلید اصلی (primary key) بازیابی کنید یا با استفاده از یک ایندکس. ایندکس به شما امکان می‌دهد رکوردها را در یک object store بر اساس ویژگی‌هایی از مقادیرِ رکوردهای همان object store جست‌وجو کنید که به‌جز کلید اصلی هستند.

ایندکس یک ذخیره‌گاه پایدار کلید-مقدار است که بخش مقدارِ رکوردهای آن، بخش کلیدِ یک رکورد در object store مرجع است. رکوردهای یک ایندکس هر زمان که رکوردهایی در object store مرجع درج، به‌روزرسانی یا حذف شوند، به‌طور خودکار پر می‌شوند. هر رکورد در یک ایندکس فقط می‌تواند به یک رکورد در object store مرجع اشاره کند؛ اما چندین ایندکس می‌توانند به یک object store اشاره کنند. هرگاه object store تغییر کند، همهٔ ایندکس‌هایی که به آن ارجاع می‌دهند به‌طور خودکار به‌روزرسانی می‌شوند.

می‌توانید مجموعه‌ای از کلیدها را در یک بازه دریافت کنید. برای اطلاعات بیشتر، {{domxref("IDBKeyRange")}} را ببینید.

## ویژگی‌های نمونه

- {{domxref("IDBIndex.isAutoLocale")}} {{ReadOnlyInline}} {{ non-standard_inline }} {{deprecated_inline}}
  - : یک مقدار بولین برمی‌گرداند که نشان می‌دهد هنگام ایجاد ایندکس، مقدار `locale` برای آن برابر با `auto` تعیین شده است یا خیر (پارامتر [`options`](/en-US/docs/Web/API/IDBObjectStore/createIndex#options) را در [`IDBObjectStore.createIndex()`](/en-US/docs/Web/API/IDBObjectStore/createIndex) ببینید).
- {{domxref("IDBIndex.locale")}} {{ReadOnlyInline}} {{ non-standard_inline }} {{deprecated_inline}}
  - : locale ایندکس را برمی‌گرداند (برای مثال `en-US` یا `pl`)، اگر هنگام ایجاد ایندکس، مقدار `locale` برای آن تعیین شده باشد.
- {{domxref("IDBIndex.name")}}
  - : نام این ایندکس.
- {{domxref("IDBIndex.objectStore")}} {{ReadOnlyInline}}
  - : نام object store‌ای که این ایندکس به آن ارجاع می‌دهد.
- {{domxref("IDBIndex.keyPath")}} {{ReadOnlyInline}}
  - : مسیر کلید (key path) این ایندکس. اگر `null` باشد، این ایندکس به‌طور خودکار پر نمی‌شود.
- {{domxref("IDBIndex.multiEntry")}} {{ReadOnlyInline}}
  - : بر رفتار ایندکس اثر می‌گذارد وقتی نتیجهٔ ارزیابی مسیر کلید ایندکس یک آرایه باشد. اگر `true` باشد، برای هر آیتم در آرایهٔ کلیدها یک رکورد در ایندکس وجود دارد. اگر `false` باشد، برای هر کلیدِ آرایه‌ای یک رکورد وجود دارد.
- {{domxref("IDBIndex.unique")}} {{ReadOnlyInline}}
  - : اگر `true` باشد، این ایندکس اجازه نمی‌دهد برای یک کلید، مقادیر تکراری وجود داشته باشد.

## متدهای نمونه

ارث‌بری از [EventTarget](/en-US/docs/Web/API/EventTarget)

- {{domxref("IDBIndex.count()")}}
  - : یک شیء {{domxref("IDBRequest")}} برمی‌گرداند و در یک ریسمان جداگانه، تعداد رکوردهای درون یک بازهٔ کلید را برمی‌گرداند.
- {{domxref("IDBIndex.get()")}}
  - : یک شیء {{domxref("IDBRequest")}} برمی‌گرداند و در یک ریسمان جداگانه، یا مقدارِ متناظر با کلید داده‌شده را در object store مرجع پیدا می‌کند، یا اگر `key` یک {{domxref("IDBKeyRange")}} باشد، نخستین مقدارِ متناظر را پیدا می‌کند.
- {{domxref("IDBIndex.getKey()")}}
  - : یک شیء {{domxref("IDBRequest")}} برمی‌گرداند و در یک ریسمان جداگانه، یا کلید داده‌شده یا کلید اصلی را پیدا می‌کند، اگر `key` یک {{domxref("IDBKeyRange")}} باشد.
- {{domxref("IDBIndex.getAll()")}}
  - : یک شیء {{domxref("IDBRequest")}} برمی‌گرداند و در یک ریسمان جداگانه، همهٔ مقادیر منطبق در object store مرجع را پیدا می‌کند که با کلید داده‌شده متناظرند یا اگر `key` یک {{domxref("IDBKeyRange")}} باشد، در بازه قرار دارند.
- {{domxref("IDBIndex.getAllKeys()")}}
  - : یک شیء {{domxref("IDBRequest")}} برمی‌گرداند و در یک ریسمان جداگانه، همهٔ کلیدهای منطبق در object store مرجع را پیدا می‌کند که با کلید داده‌شده متناظرند یا اگر `key` یک {{domxref("IDBKeyRange")}} باشد، در بازه قرار دارند.
- {{domxref("IDBIndex.getAllRecords()")}}
  - : یک شیء {{domxref("IDBRequest")}} برمی‌گرداند و در یک ریسمان جداگانه، همهٔ رکوردهای منطبق در object store مرجع (شامل کلیدهای ایندکس، کلیدهای اصلی و مقادیر) را پیدا می‌کند که با کلید داده‌شده متناظرند یا اگر `key` یک {{domxref("IDBKeyRange")}} باشد، در بازه قرار دارند.
- {{domxref("IDBIndex.openCursor()")}}
  - : یک شیء {{domxref("IDBRequest")}} برمی‌گرداند و در یک ریسمان جداگانه، یک [cursor](/en-US/docs/Web/API/IndexedDB_API/Basic_Terminology#cursor) بر روی بازهٔ کلید مشخص‌شده ایجاد می‌کند.
- {{domxref("IDBIndex.openKeyCursor()")}}
  - : یک شیء {{domxref("IDBRequest")}} برمی‌گرداند و در یک ریسمان جداگانه، یک cursor بر روی بازهٔ کلید مشخص‌شده، به ترتیبی که توسط این ایندکس مرتب شده است، ایجاد می‌کند.

## مثال

در مثال زیر یک تراکنش و یک object store را باز می‌کنیم و سپس ایندکس `lName` را از یک پایگاه‌دادهٔ سادهٔ مخاطبین دریافت می‌کنیم. سپس با استفاده از {{domxref("IDBIndex.openCursor")}} یک cursor ساده روی ایندکس باز می‌کنیم — این کار دقیقاً مانند باز کردن cursor مستقیم روی یک `ObjectStore` با استفاده از {{domxref("IDBObjectStore.openCursor")}} عمل می‌کند، با این تفاوت که رکوردهای بازگشتی بر اساس ایندکس مرتب می‌شوند، نه کلید اصلی.

در پایان، روی هر رکورد پیمایش می‌کنیم و داده‌ها را در یک جدول HTML وارد می‌کنیم. برای مشاهدهٔ مثال کامل و قابل اجرا، [مخزن دموی IndexedDB-examples](https://github.com/mdn/dom-examples/tree/main/indexeddb-examples/idbindex) را ببینید. ([مشاهدهٔ مثال زنده](https://mdn.github.io/dom-examples/indexeddb-examples/idbindex/))

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

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم بازه‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و اعمال تغییرات روی داده‌ها: {{domxref("IDBObjectStore")}}
- استفاده از cursorها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهدهٔ مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
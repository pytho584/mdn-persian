---
title: "IDBObjectStore: createIndex() method"
short-title: createIndex()
slug: Web/API/IDBObjectStore/createIndex
page-type: web-api-instance-method
browser-compat: api.IDBObjectStore.createIndex
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

متد **`createIndex()`** از رابط {{domxref("IDBObjectStore")}} یک شیء جدید {{domxref("IDBIndex")}} در پایگاه‌دادهٔ متصل‌شده ایجاد کرده و برمی‌گرداند. این متد یک فیلد/ستون جدید تعریف می‌کند که یک نقطه‌دادهٔ جدید را برای هر رکورد از پایگاه‌داده مشخص می‌کند.

توجه داشته باشید که ایندکس‌های IndexedDB می‌توانند _هر_ نوع داده‌ای در جاوااسکریپت را شامل شوند؛ IndexedDB از [الگوریتم شبیه‌سازی ساختاریافته](/en-US/docs/Web/API/Web_Workers_API/Structured_clone_algorithm) برای سریال‌سازی اشیاء ذخیره‌شده استفاده می‌کند که امکان ذخیره‌سازی اشیاء ساده و پیچیده را فراهم می‌کند.

توجه داشته باشید که این متد فقط باید از یک تابع بازخوانی (callback) در حالت تراکنش `VersionChange` فراخوانی شود.

## Syntax

```js-nolint
createIndex(indexName, keyPath)
createIndex(indexName, keyPath, options)
```

### Parameters

- `indexName`
  - : نام ایندکسی که قرار است ساخته شود. توجه داشته باشید که امکان ایجاد ایندکس با نام خالی نیز وجود دارد.
- `keyPath`
  - : مسیر کلید (keyPath) مورد استفاده برای ایندکس. توجه داشته باشید که امکان ایجاد ایندکس با `keyPath` خالی وجود دارد و همچنین می‌توان یک دنباله (آرایه) را به‌عنوان `keyPath` ارسال کرد.
- `options` {{optional_inline}}
  - : یک شیء که می‌تواند ویژگی‌های زیر را شامل شود:
    - `unique`
      - : اگر `true` باشد، ایندکس برای یک کلید واحد مقادیر تکراری را مجاز نخواهد داشت. پیش‌فرض `false` است.
    - `multiEntry`
      - : اگر `true` باشد، وقتی `keyPath` به یک آرایه منجر شود، ایندکس برای هر عنصر آرایه یک ورودی اضافه می‌کند.
        اگر `false` باشد، یک ورودی واحد شامل کل آرایه اضافه می‌کند. پیش‌فرض `false` است.
    - `locale` {{non-standard_inline}} {{deprecated_inline}}
      - : به شما امکان می‌دهد یک locale (محل/زبان) برای ایندکس مشخص کنید. هرگونه عملیات مرتب‌سازی انجام‌شده روی داده‌ها از طریق بازه‌های کلید (key ranges) از قوانین مرتب‌سازی آن locale پیروی می‌کند.
        می‌توانید مقدار آن را به یکی از سه روش زیر تعیین کنید:
        - `string`: رشته‌ای شامل یک کد locale خاص، مانند `en-US` یا `pl`.
        - `auto`: از locale پیش‌فرض پلتفرم استفاده خواهد شد (ممکن است توسط تنظیمات عامل کاربر تغییر کند).
        - `null` یا `undefined`: اگر locale مشخص نشود، از مرتب‌سازی معمولی جاوااسکریپت استفاده می‌شود — بدون آگاهی از locale.

### Return value

یک شیء {{domxref("IDBIndex")}}: ایندکس تازه ایجاد شده.

### Exceptions

این متد ممکن است یک {{domxref("DOMException")}} از یکی از انواع زیر صادر کند:

- `ConstraintError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که ایندکسی با همان نام از قبل در پایگاه‌داده وجود داشته باشد. نام ایندکس‌ها به حروف بزرگ و کوچک حساس هستند.
- `InvalidAccessError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که keyPath ارائه‌شده یک دنباله (sequence) باشد و `multiEntry` در شیء `objectParameters` روی `true` تنظیم شده باشد.
- `InvalidStateError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که:
    - متد از یک تابع بازخوانی در حالت تراکنش `versionchange` فراخوانی نشده باشد، یعنی از داخل یک کنترل‌کنندهٔ {{domxref("IDBOpenDBRequest.upgradeneeded_event", "onupgradeneeded")}}.
    - object store حذف شده باشد.
- `SyntaxError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که `keyPath` ارائه‌شده یک [مسیر کلید معتبر](https://w3c.github.io/IndexedDB/#valid-key-path) نباشد.
- `TransactionInactiveError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که تراکنشی که این {{domxref("IDBObjectStore")}} به آن تعلق دارد فعال نباشد (مثلاً حذف شده یا برداشته شده باشد). در فایرفاکس پیش از نسخهٔ 41، در این حالت همچنین یک `InvalidStateError` صادر می‌شد که گمراه‌کننده بود؛ این مشکل اکنون برطرف شده است (به [باگ 1176165 فایرفاکس](https://bugzil.la/1176165) مراجعه کنید).

## Examples

در مثال زیر، می‌بینید که از کنترل‌کنندهٔ {{domxref("IDBOpenDBRequest.upgradeneeded_event", "onupgradeneeded")}} برای به‌روزرسانی ساختار پایگاه‌داده استفاده می‌شود، در صورتی که پایگاه‌داده‌ای با شماره نسخهٔ بالاتر بارگذاری شده باشد. از `createIndex()` برای ایجاد ایندکس‌های جدید روی object store استفاده می‌شود. برای مشاهدهٔ یک مثال کامل و قابل اجرا، اپلیکیشن [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) را ببینید ([مشاهدهٔ مثال آنلاین](https://mdn.github.io/dom-examples/to-do-notifications/)).

```js
let db;

// Let us open our database
const DBOpenRequest = window.indexedDB.open("toDoList", 4);

// Two event handlers for opening the database.
DBOpenRequest.onerror = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Error loading database.";
};

DBOpenRequest.onsuccess = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Database initialized.";

  // store the result of opening the database in the db variable.
  // This is used a lot below.
  db = request.result;

  // Run the displayData() function to populate the task list with
  // all the to-do list data already in the IDB
  displayData();
};

// This handler fires when a new database is created and indicates
// either that one has not been created before, or a new version
// was submitted with window.indexedDB.open(). (See above.)
// It is only implemented in recent browsers.
DBOpenRequest.onupgradeneeded = (event) => {
  const db = event.target.result;

  db.onerror = (event) => {
    note.appendChild(document.createElement("li")).textContent =
      "Error loading database.";
  };

  // Create an objectStore for this database
  const objectStore = db.createObjectStore("toDoList", {
    keyPath: "taskTitle",
  });

  // define what data items the objectStore will contain

  objectStore.createIndex("hours", "hours", { unique: false });
  objectStore.createIndex("minutes", "minutes", { unique: false });
  objectStore.createIndex("day", "day", { unique: false });
  objectStore.createIndex("month", "month", { unique: false });
  objectStore.createIndex("year", "year", { unique: false });
  objectStore.createIndex("notified", "notified", { unique: false });
};
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
- بازیابی و تغییر داده‌ها: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها (cursors): {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهدهٔ مثال آنلاین](https://mdn.github.io/dom-examples/to-do-notifications/)).
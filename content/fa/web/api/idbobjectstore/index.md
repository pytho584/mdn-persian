---
title: IDBObjectStore
slug: Web/API/IDBObjectStore
page-type: web-api-interface
browser-compat: api.IDBObjectStore
---

{{APIRef("IndexedDB")}} {{AvailableInWorkers}}

رابطِ **`IDBObjectStore`** در [IndexedDB API](/en-US/docs/Web/API/IndexedDB_API) نمایانگر یک مخزن آبجکت (object store) در پایگاه‌داده است. رکوردهای درون یک مخزن آبجکت بر اساس کلیدهایشان مرتب می‌شوند. این مرتب‌سازی، درج سریع، جست‌وجو، و بازیابیِ مرتب‌شده را ممکن می‌سازد.

## ویژگی‌های نمونه

- {{domxref("IDBObjectStore.indexNames")}} {{ReadOnlyInline}}
  - : فهرستی از نام «ایندکس»های مربوط به اشیای موجود در این مخزن آبجکت.
- {{domxref("IDBObjectStore.keyPath")}} {{ReadOnlyInline}}
  - : [مسیر کلید](/en-US/docs/Web/API/IndexedDB_API/Basic_Terminology#key_path) این مخزن آبجکت. اگر این ویژگی `null` باشد، برنامه باید برای هر عملیات تغییر، یک کلید فراهم کند.
- {{domxref("IDBObjectStore.name")}}
  - : نام این مخزن آبجکت.
- {{domxref("IDBObjectStore.transaction")}} {{ReadOnlyInline}}
  - : شیء {{domxref("IDBTransaction")}} ای که این مخزن آبجکت به آن تعلق دارد.
- {{domxref("IDBObjectStore.autoIncrement")}} {{ReadOnlyInline}}
  - : مقدار پرچم خودافزایش (auto increment) برای این مخزن آبجکت.

## متدهای نمونه

- {{domxref("IDBObjectStore.add()")}}
  - : یک شیء {{domxref("IDBRequest")}} برمی‌گرداند و در یک نخ جداگانه، یک [کپی ساختاریافته (structured clone)](https://html.spec.whatwg.org/multipage/common-dom-interfaces.html#structured-clone) از `value` می‌سازد و مقدار کپی‌شده را در مخزن آبجکت ذخیره می‌کند. از این متد برای افزودن رکوردهای جدید به یک مخزن آبجکت استفاده می‌شود.
- {{domxref("IDBObjectStore.clear()")}}
  - : یک شیء {{domxref("IDBRequest")}} می‌سازد و بلافاصله آن را برمی‌گرداند و در یک نخ جداگانه، این مخزن آبجکت را پاک می‌کند. از این متد برای حذف همهٔ رکوردهای فعلی از یک مخزن آبجکت استفاده می‌شود.
- {{domxref("IDBObjectStore.count()")}}
  - : یک شیء {{domxref("IDBRequest")}} برمی‌گرداند و در یک نخ جداگانه، تعداد کل رکوردهایی را برمی‌گرداند که با کلید داده‌شده یا {{domxref("IDBKeyRange")}} مطابقت دارند. اگر آرگومانی ارسال نشود، تعداد کل رکوردهای مخزن را برمی‌گرداند.
- {{domxref("IDBObjectStore.createIndex()")}}
  - : ایندکس جدیدی را در هنگام ارتقای نسخه می‌سازد و یک شیء {{domxref("IDBIndex")}} جدید را در پایگاه‌دادهٔ متصل برمی‌گرداند.
- {{domxref("IDBObjectStore.delete()")}}
  - : یک شیء {{domxref("IDBRequest")}} برمی‌گرداند و در یک نخ جداگانه، رکورد انتخاب‌شده با کلید مشخص‌شده را از مخزن آبجکت حذف می‌کند. از این متد برای حذف رکوردهای تکی از یک مخزن آبجکت استفاده می‌شود.
- {{domxref("IDBObjectStore.deleteIndex()")}}
  - : ایندکس مشخص‌شده را در پایگاه‌دادهٔ متصل از بین می‌برد؛ در هنگام ارتقای نسخه استفاده می‌شود.
- {{domxref("IDBObjectStore.get()")}}
  - : یک شیء {{domxref("IDBRequest")}} برمی‌گرداند و در یک نخ جداگانه، رکورد انتخاب‌شده با کلید مشخص‌شده را برمی‌گرداند. از این متد برای بازیابی رکوردهای خاص از یک مخزن آبجکت استفاده می‌شود.
- {{domxref("IDBObjectStore.getKey()")}}
  - : یک شیء {{domxref("IDBRequest")}} برمی‌گرداند و در یک نخ جداگانه، کلیدِ رکوردِ شیءِ موجود در مخزن آبجکت را که با پارامتر مشخص‌شده مطابقت دارد، بازیابی و برمی‌گرداند.
- {{domxref("IDBObjectStore.getAll()")}}
  - : یک شیء {{domxref("IDBRequest")}} برمی‌گرداند و در یک نخ جداگانه، همهٔ اشیای موجود در مخزن آبجکت را که با پارامتر مشخص‌شده مطابقت دارند بازیابی می‌کند؛ اگر پارامتری داده نشود، همهٔ اشیای مخزن را برمی‌گرداند.
- {{domxref("IDBObjectStore.getAllKeys()")}}
  - : یک شیء {{domxref("IDBRequest")}} برمی‌گرداند و در یک نخ جداگانه، کلیدِ رکوردِ همهٔ اشیای موجود در مخزن آبجکت را که با پارامتر مشخص‌شده مطابقت دارند بازیابی می‌کند؛ اگر پارامتری داده نشود، کلیدِ رکوردِ همهٔ اشیای مخزن را برمی‌گرداند.
- {{domxref("IDBObjectStore.getAllRecords()")}}
  - : یک شیء {{domxref("IDBRequest")}} برمی‌گرداند و در یک نخ جداگانه، همهٔ رکوردهای منطبق در مخزن آبجکت (شامل کلیدهای اصلی و مقادیر) را می‌یابد که با کلید داده‌شده مطابقت دارند یا، اگر `key` یک {{domxref("IDBKeyRange")}} باشد، در محدودهٔ آن قرار می‌گیرند.
- {{domxref("IDBObjectStore.index()")}}
  - : یک ایندکس را از این مخزن آبجکت باز می‌کند؛ پس از آن می‌توان برای مثال با استفاده از یک کرسر، دنباله‌ای از رکوردها را که بر اساس آن ایندکس مرتب شده‌اند بازگرداند.
- {{domxref("IDBObjectStore.openCursor()")}}
  - : یک شیء {{domxref("IDBRequest")}} برمی‌گرداند و در یک نخ جداگانه، یک شیء جدید {{domxref("IDBCursorWithValue")}} برمی‌گرداند. برای پیمایش یک مخزن آبجکت بر اساس کلید اصلی با کرسر استفاده می‌شود.
- {{domxref("IDBObjectStore.openKeyCursor()")}}
  - : یک شیء {{domxref("IDBRequest")}} برمی‌گرداند و در یک نخ جداگانه، یک {{domxref("IDBCursor")}} جدید برمی‌گرداند. برای پیمایش یک مخزن آبجکت با کلید استفاده می‌شود.
- {{domxref("IDBObjectStore.put()")}}
  - : یک شیء {{domxref("IDBRequest")}} برمی‌گرداند و در یک نخ جداگانه، یک [کپی ساختاریافته (structured clone)](https://html.spec.whatwg.org/multipage/common-dom-interfaces.html#structured-clone) از `value` می‌سازد و مقدار کپی‌شده را در مخزن آبجکت ذخیره می‌کند. از این متد برای به‌روزرسانی رکوردهای موجود در یک مخزن آبجکت زمانی استفاده می‌شود که حالت تراکنش `readwrite` باشد.

## مثال

این مثال کاربردهای گوناگون مخزن‌های آبجکت را نشان می‌دهد؛ از به‌روزرسانی ساختار داده با {{domxref("IDBObjectStore.createIndex")}} درون تابع `onupgradeneeded` تا افزودن یک آیتم جدید به مخزن آبجکت با {{domxref("IDBObjectStore.add")}}. برای مشاهدهٔ مثال کامل و قابل اجرا، به برنامهٔ [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) مراجعه کنید ([مشاهدهٔ مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).

```js
// Let us open our database
const DBOpenRequest = window.indexedDB.open("toDoList", 4);

DBOpenRequest.onsuccess = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Database initialized.";

  // store the result of opening the database in db.
  db = DBOpenRequest.result;
};

// This event handles the event whereby a new version of
// the database needs to be created Either one has not
// been created before, or a new version number has been
// submitted via the window.indexedDB.open line above
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

  note.appendChild(document.createElement("li")).textContent =
    "Object store created.";
};

// Create a new item to add in to the object store
const newItem = [
  {
    taskTitle: "Walk dog",
    hours: 19,
    minutes: 30,
    day: 24,
    month: "December",
    year: 2013,
    notified: "no",
  },
];

// open a read/write db transaction, ready for adding the data
const transaction = db.transaction(["toDoList"], "readwrite");

// report on the success of the transaction completing, when everything is done
transaction.oncomplete = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Transaction completed.";
};

transaction.onerror = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Transaction not opened due to error. Duplicate items not allowed.";
};

// create an object store on the transaction
const objectStore = transaction.objectStore("toDoList");
// make a request to add our newItem object to the object store
const objectStoreRequest = objectStore.add(newItem[0]);

objectStoreRequest.onsuccess = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Request successful.";
};
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
- استفاده از کرسرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهدهٔ مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
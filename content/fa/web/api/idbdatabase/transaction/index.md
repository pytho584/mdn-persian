---
title: "IDBDatabase: transaction() method"
short-title: transaction()
slug: Web/API/IDBDatabase/transaction
page-type: web-api-instance-method
browser-compat: api.IDBDatabase.transaction
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

متد **`transaction`** در رابط {{domxref("IDBDatabase")}} بلافاصله یک شیء تراکنش ({{domxref("IDBTransaction")}}) برمی‌گرداند که حاوی متد {{domxref("IDBTransaction.objectStore")}} است و می‌توانید از آن برای دسترسی به object store خود استفاده کنید.

## نحو (Syntax)

```js-nolint
transaction(storeNames)
transaction(storeNames, mode)
transaction(storeNames, mode, options)
```

### پارامترها

- `storeNames`
  - نام object storeهایی که در محدوده تراکنش جدید قرار دارند، به‌صورت یک آرایه از رشته‌ها اعلام می‌شوند. فقط object storeهایی را مشخص کنید که به آن‌ها نیاز دارید.
    اگر فقط به یک object store نیاز دارید، می‌توانید نام آن را به‌صورت یک رشته مشخص کنید.
    بنابراین خطوط زیر معادل هستند:

    ```js
    db.transaction(["my-store-name"]);
    db.transaction("my-store-name");
    ```

    اگر نیاز به دسترسی به همه object storeهای پایگاه داده دارید، می‌توانید از ویژگی {{domxref("IDBDatabase.objectStoreNames")}} استفاده کنید:

    ```js
    const transaction = db.transaction(db.objectStoreNames);
    ```

    عبور دادن یک آرایه خالی باعث ایجاد استثنا خواهد شد.

- `mode` {{optional_inline}}
  - انواع دسترسی که می‌توان در تراکنش انجام داد.
    تراکنش‌ها در یکی از سه حالت باز می‌شوند:
    - `readonly`
      - یک تراکنش برای خواندن از یک object store باز می‌کند. این حالت پیش‌فرض است.
    - `readwrite`
      - یک تراکنش برای خواندن و نوشتن در یک object store باز می‌کند. این حالت فقط در صورتی باید استفاده شود که نیاز به نوشتن در پایگاه داده دارید.
    - `readwriteflush` {{non-standard_inline}} {{experimental_inline}}
      - تراکنش را مجبور می‌کند قبل از تحویل رویداد `complete` روی دیسک flush شود. این حالت ممکن است برای ذخیره داده‌های حیاتی که نمی‌توان بعداً آن‌ها را دوباره محاسبه کرد استفاده شود.

- `options` {{optional_inline}}
  - شیئی که گزینه‌های اضافی را تعریف می‌کند، از جمله:
    - `durability`
      - یکی از سه مقدار رشته‌ای (string literal) زیر:
        - `"strict"`
          - عامل کاربر ممکن است تنها پس از تأیید اینکه همه تغییرات باقی‌مانده با موفقیت در یک رسانه ذخیره‌سازی پایدار نوشته شده‌اند، تراکنش را با موفقیت commit شده در نظر بگیرد. این حالت در جایی توصیه می‌شود که خطر از دست رفتن داده‌ها بیشتر از تأثیر استفاده از آن بر عملکرد و مصرف انرژی (در مقایسه با `relaxed`) باشد.
        - `"relaxed"`
          - عامل کاربر ممکن است به محض اینکه همه تغییرات باقی‌مانده در سیستم‌عامل نوشته شدند، بدون تأیید بعدی، تراکنش را با موفقیت commit شده در نظر بگیرد. این حالت عملکرد بهتری نسبت به `strict` ارائه می‌دهد و برای داده‌های موقتی مانند کش‌ها یا رکوردهایی که به‌سرعت تغییر می‌کنند توصیه می‌شود.
        - `"default"`
          - عامل کاربر باید رفتار پیش‌فرض خود را برای ماندگاری (durability) در سطل ذخیره‌سازی (storage bucket) استفاده کند. این حالت برای تراکنش‌ها اگر طور دیگری مشخص نشده باشد، پیش‌فرض است.

### مقدار بازگشتی

یک شیء {{domxref("IDBTransaction")}}.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - اگر متد {{domxref("IDBDatabase.close", "close()")}} قبلاً روی این نمونه از {{domxref("IDBDatabase")}} فراخوانی شده باشد، پرتاب می‌شود.
- `NotFoundError` {{domxref("DOMException")}}
  - اگر یک object store که در پارامتر 'storeNames' مشخص شده است حذف یا برداشته شده باشد، پرتاب می‌شود.
- {{jsxref("TypeError")}}
  - اگر مقدار پارامتر `mode` نامعتبر باشد، پرتاب می‌شود.
- `InvalidAccessError` {{domxref("DOMException")}}
  - اگر تابع با فهرست خالی از نام‌های store فراخوانی شود، پرتاب می‌شود.

## مثال‌ها

در این مثال یک اتصال پایگاه داده باز می‌کنیم و سپس از transaction() برای باز کردن یک تراکنش روی پایگاه داده استفاده می‌کنیم.
برای مثال کامل، برنامه [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) را ببینید ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).

```js
let db;

// Let us open our database
const DBOpenRequest = window.indexedDB.open("toDoList", 4);

DBOpenRequest.onsuccess = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Database initialized.";

  // store the result of opening the database in the db variable.
  // This is used a lot below
  db = DBOpenRequest.result;

  // Run the displayData() function to populate the task list with
  // all the to-do list data already in the IDB
  displayData();
};

// open a read/write db transaction, ready for adding the data
const transaction = db.transaction(["toDoList"], "readwrite");

// report on the success of opening the transaction
transaction.oncomplete = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Transaction completed: database modification finished.";
};

transaction.onerror = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Transaction not opened due to error. Duplicate items not allowed.";
};

// you would then go on to do something to this database
// via an object store
const objectStore = transaction.objectStore("toDoList");
// etc.
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
- بازیابی و ایجاد تغییرات در داده‌های خود: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها (cursors): {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
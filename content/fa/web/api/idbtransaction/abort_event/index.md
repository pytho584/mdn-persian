---
title: "IDBTransaction: abort event"
short-title: abort
slug: Web/API/IDBTransaction/abort_event
page-type: web-api-event
browser-compat: api.IDBTransaction.abort_event
---

{{APIRef("IndexedDB")}}

رویداد `abort` زمانی رخ می‌دهد که یک تراکنش `IndexedDB` لغو شود.

این رویداد می‌تواند به دلایل زیر رخ دهد:

- درخواست‌های نامعتبر (مثلاً تلاش برای افزودن کلید تکراری، یا قرار دادن کلید ایندکس یکسان در حالی که کلید دارای محدودیت یکتایی است).
- فراخوانی صریح {{DOMxRef("IDBTransaction.abort", "abort()")}}.
- یک استثنای مدیریت‌نشده در هندلر موفقیت/خطای درخواست.
- خطای ورودی/خروجی (مثلاً شکست واقعی در نوشتن روی دیسک، مانند جدا شدن دیسک یا سایر خرابی‌های سیستم‌عامل/سخت‌افزار).
- تجاوز از سهمیه ذخیره‌سازی.

این رویداد غیرقابل‌لغو، به شیء {{domxref("IDBDatabase")}} مرتبط [حباب می‌شود](/en-US/docs/Learn_web_development/Core/Scripting/Event_bubbling).

## نحو (Syntax)

برای استفاده، نام رویداد را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به کار ببرید، یا یک ویژگی مدیریت رویداد تنظیم کنید.

```js-nolint
addEventListener("abort", (event) => { })

onabort = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## حباب‌زنی

این رویداد به `IDBDatabase` حباب می‌شود. ویژگی `event.target` به شیء {{domxref('IDBTransaction')}} اشاره می‌کند که به سمت بالا حباب می‌شود.

برای اطلاعات بیشتر، [حباب‌زنی رویداد](/en-US/docs/Learn_web_development/Core/Scripting/Event_bubbling) را ببینید.

## مثال‌ها

این مثال یک پایگاه داده را باز می‌کند (اگر وجود نداشته باشد آن را می‌سازد)، سپس یک تراکنش باز می‌کند، یک شنونده روی رویداد `abort` اضافه می‌کند و سپس تراکنش را لغو می‌کند تا رویداد رخ دهد.

```js
// Open the database
const DBOpenRequest = window.indexedDB.open("toDoList", 4);

DBOpenRequest.onupgradeneeded = (event) => {
  const db = event.target.result;

  db.onerror = () => {
    console.log("Error creating database");
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
};

DBOpenRequest.onsuccess = (event) => {
  const db = DBOpenRequest.result;

  // open a read/write db transaction, ready for adding the data
  const transaction = db.transaction(["toDoList"], "readwrite");

  // add a listener for `abort`
  transaction.addEventListener("abort", () => {
    console.log("Transaction was aborted");
  });

  // abort the transaction
  transaction.abort();
};
```

مثال مشابه، اما با انتساب مدیریت رویداد به ویژگی `onabort`:

```js
// Open the database
const DBOpenRequest = window.indexedDB.open("toDoList", 4);

DBOpenRequest.onupgradeneeded = (event) => {
  const db = event.target.result;

  db.onerror = () => {
    console.log("Error creating database");
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
};

DBOpenRequest.onsuccess = (event) => {
  const db = DBOpenRequest.result;

  // open a read/write db transaction, ready for adding the data
  const transaction = db.transaction(["toDoList"], "readwrite");

  // add a listener for `abort`
  transaction.onabort = (event) => {
    console.log("Transaction was aborted");
  };

  // abort the transaction
  transaction.abort();
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
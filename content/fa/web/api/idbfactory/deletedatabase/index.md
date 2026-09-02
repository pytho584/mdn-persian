---
title: "IDBFactory: deleteDatabase() method"
short-title: deleteDatabase()
slug: Web/API/IDBFactory/deleteDatabase
page-type: web-api-instance-method
browser-compat: api.IDBFactory.deleteDatabase
---

{{APIRef("IndexedDB")}} {{AvailableInWorkers}}

متد **`deleteDatabase()`** از رابط {{DOMxRef("IDBFactory")}} درخواست حذف یک پایگاه داده را می‌دهد. این متد بلافاصله یک شیء {{DOMxRef("IDBOpenDBRequest")}} برمی‌گرداند و عملیات حذف را به‌صورت ناهمزمان انجام می‌دهد.

اگر پایگاه داده با موفقیت حذف شود، رویداد `success` روی شیء درخواست بازگشتی از این متد فعال می‌شود و `result` آن برابر `undefined` قرار می‌گیرد. اگر در حین حذف پایگاه داده خطایی رخ دهد، رویداد `error` روی شیء درخواست بازگشتی فعال می‌شود.

هنگامی که `deleteDatabase()` فراخوانی می‌شود، هر اتصال باز دیگری به این پایگاه داده خاص یک رویداد [versionchange](/en-US/docs/Web/API/IDBDatabase/versionchange_event) دریافت می‌کند.

## نحو (Syntax)

```js-nolint
// برای استاندارد فعلی:
deleteDatabase(name)

// برای نسخه آزمایشی با `options` (به زیر مراجعه کنید):
deleteDatabase(name)
deleteDatabase(name, options)
```

### پارامترها

- `name`
  - : نام پایگاه داده‌ای که می‌خواهید حذف کنید. توجه داشته باشید که تلاش برای حذف یک پایگاه داده که وجود ندارد، برخلاف {{DOMxRef("IDBDatabase.deleteObjectStore()")}} که در صورت عدم وجود ذخیره‌گاه شیء نام‌برده شده استثنا پرتاب می‌کند، در اینجا استثنا پرتاب نمی‌کند.
- `options` {{optional_inline}} {{Non-standard_Inline}}
  - : در Gecko، از [نسخه 26](/en-US/docs/Mozilla/Firefox/Releases/26) به بعد، می‌توانید یک پارامتر ذخیره‌سازی غیراستاندارد اختیاری اضافه کنید که مشخص می‌کند آیا می‌خواهید یک IndexedDB `permanent` (مقدار پیش‌فرض) را حذف کنید یا یک indexedDB در ذخیره‌سازی `temporary` (معروف به حافظه اشتراکی).

### مقدار بازگشتی

یک {{DOMxRef("IDBOpenDBRequest")} که رویدادهای بعدی مربوط به این درخواست روی آن فعال می‌شوند. اگر عملیات موفقیت‌آمیز باشد، مقدار ویژگی {{domxref("IDBRequest.result", "result")}} درخواست `null` خواهد بود.

## مثال‌ها

```js
const DBDeleteRequest = window.indexedDB.deleteDatabase("toDoList");

DBDeleteRequest.onerror = (event) => {
  console.error("Error deleting database.");
};

DBDeleteRequest.onsuccess = (event) => {
  console.log("Database deleted successfully");

  console.log(event.result); // should be undefined
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{DOMxRef("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{DOMxRef("IDBTransaction")}}
- تنظیم محدوده کلیدها: {{DOMxRef("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌های خود: {{DOMxRef("IDBObjectStore")}}
- استفاده از نشانگرها: {{DOMxRef("IDBCursor")}}
- مثال مرجع: [اعلان‌های کارهای روزانه](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
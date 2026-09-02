---
title: "IDBDatabase: close() method"
---

---
title: "IDBDatabase: close() method"
short-title: close()
slug: Web/API/IDBDatabase/close
page-type: web-api-instance-method
browser-compat: api.IDBDatabase.close
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

متد **`close()`** در رابط {{domxref("IDBDatabase")}} بلافاصله باز می‌گردد و اتصال را در یک رشتهٔ اجرایی جداگانه می‌بندد.

اتصال در عمل بسته نخواهد شد، مگر پس از کامل شدن همهٔ تراکنش‌های ایجادشده با این اتصال. پس از فراخوانی این متد، دیگر نمی‌توان تراکنش جدیدی برای این اتصال ایجاد کرد. اگر عملیات بستن هنوز به پایان نرسیده باشد، متدهایی که تراکنش ایجاد می‌کنند، یک استثنا پرتاب می‌کنند.

## سینتکس

```js-nolint
close()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مثال‌ها

```js
// Let us open our database
const DBOpenRequest = window.indexedDB.open("toDoList", 4); // opening a database.

// Create event handlers for both success and failure of
DBOpenRequest.onerror = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Error loading database.";
};

DBOpenRequest.onsuccess = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Database initialized.";

  // store the result of opening the database in the db variable.
  db = DBOpenRequest.result;

  // now let's close the database again!
  db.close();
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم بازه‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و اعمال تغییرات در داده‌ها: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهدهٔ مثال به‌صورت زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
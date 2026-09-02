---
title: "IDBTransaction: commit() method"
short-title: commit()
slug: Web/API/IDBTransaction/commit
page-type: web-api-instance-method
browser-compat: api.IDBTransaction.commit
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

متد **`commit()`** از رابط {{domxref("IDBTransaction")}}، اگر روی یک تراکنش فعال فراخوانی شود، تراکنش را commit می‌کند.

توجه داشته باشید که به‌طور معمول _لزومی_ به فراخوانی `commit()` نیست؛ وقتی همهٔ درخواست‌های در انتظار برآورده شده باشند و درخواست جدیدی نیز مطرح نشده باشد، تراکنش به‌طور خودکار commit می‌شود. از `commit()` می‌توان برای شروع فرایند commit بدون انتظار برای ارسال رویدادهای درخواست‌های در انتظار استفاده کرد.

اگر روی تراکنشی که فعال نیست فراخوانی شود، یک `InvalidStateError` {{domxref("DOMException")}} پرتاب می‌کند.

## نحو

```js-nolint
commit()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر وضعیت تراکنش فعال نباشد پرتاب می‌شود.

## مثال‌ها

```js
const note = document.getElementById("notifications");

// open a read/write db transaction, ready for adding the data
const transaction = db.transaction(["myDB"], "readwrite");

// report on the success of opening the transaction
transaction.oncomplete = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Transaction completed: database modification finished.";
};

transaction.onerror = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Transaction not opened due to error. Duplicate items not allowed.";
};

// create an object store on the transaction
const objectStore = transaction.objectStore("myObjStore");

// add our newItem object to the object store
const objectStoreRequest = objectStore.add(newItem[0]);

objectStoreRequest.onsuccess = (event) => {
  // report the success of the request (this does not mean the item
  // has been stored successfully in the DB - for that you need transaction.onsuccess)
  note.appendChild(document.createElement("li")).textContent =
    "Request successful.";
};

// Force the changes to be committed to the database asap
transaction.commit();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم محدودهٔ کلیدها: {{domxref("IDBKeyRange")}}
- دریافت و ایجاد تغییرات در داده‌هایتان: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهدهٔ مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
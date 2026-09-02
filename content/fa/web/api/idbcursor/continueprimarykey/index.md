---
title: "IDBCursor: continuePrimaryKey() method"
short-title: continuePrimaryKey()
slug: Web/API/IDBCursor/continuePrimaryKey
page-type: web-api-instance-method
browser-compat: api.IDBCursor.continuePrimaryKey
---

{{APIRef("IndexedDB")}} {{AvailableInWorkers}}

روش **`continuePrimaryKey()`** از رابط {{domxref("IDBCursor")}} نشانگر را به آیتمی می‌برد که کلید آن با پارامتر کلید و همچنین کلید اصلی آن با پارامتر کلید اصلی مطابقت دارد.

یک مورد استفاده معمول، از سرگیری تکرار از جایی است که نشانگر قبلی بسته شده است، بدون نیاز به مقایسه کلیدها یکی یکی.

فراخوانی این روش بیش از یک بار قبل از بارگذاری داده‌های جدید نشانگر - به عنوان مثال، فراخوانی `continuePrimaryKey()` دو بار از یک مدیریت‌کننده onsuccess - منجر به پرتاب شدن `InvalidStateError` در فراخوانی دوم می‌شود، زیرا پرچم got value نشانگر بازنشانی شده است.

این روش فقط برای نشانگرهایی معتبر است که از یک ایندکس می‌آیند. استفاده از آن برای نشانگرهایی که از یک ذخیره‌گاه شیء می‌آیند، خطا ایجاد می‌کند.

## نحو

```js-nolint
continuePrimaryKey(key, primaryKey)
```

### پارامترها

- `key`
  - : کلیدی که نشانگر در آن قرار می‌گیرد.
- `primaryKey`
  - : کلید اصلی که نشانگر در آن قرار می‌گیرد.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### استثناها

این روش ممکن است یک {{domxref("DOMException")}} از یکی از انواع زیر را پرتاب کند:

- `TransactionInactiveError` {{domxref("DOMException")}}
  - : اگر تراکنش این `IDBCursor` غیرفعال باشد، پرتاب می‌شود.
- `DataError` {{domxref("DOMException")}}
  - : اگر پارامتر کلید هر یک از شرایط زیر را داشته باشد، پرتاب می‌شود:
    - کلید معتبر نیست.
    - کلید کمتر یا برابر با موقعیت این نشانگر است و جهت نشانگر `next` یا `nextunique` است.
    - کلید بزرگتر یا برابر با موقعیت این نشانگر است و جهت نشانگر `prev` یا `prevunique` است.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر نشانگر در حال حاضر در حال تکرار است یا از انتهای خود گذشته است، پرتاب می‌شود.
- `InvalidAccessError` {{domxref("DOMException")}}
  - : اگر جهت نشانگر `prev` یا `next` نباشد، پرتاب می‌شود.

## مثال‌ها

در اینجا نحوه از سرگیری تکرار همه مقالات برچسب‌گذاری شده با `"javascript"` از زمان آخرین بازدید شما آورده شده است:

```js
let request = articleStore.index("tag").openCursor();
let count = 0;
let unreadList = [];
request.onsuccess = (event) => {
  let cursor = event.target.result;
  if (!cursor) {
    return;
  }
  let lastPrimaryKey = getLastIteratedArticleId();
  if (lastPrimaryKey > cursor.primaryKey) {
    cursor.continuePrimaryKey("javascript", lastPrimaryKey);
    return;
  }
  // update lastIteratedArticleId
  setLastIteratedArticleId(cursor.primaryKey);
  // preload 5 articles into the unread list;
  unreadList.push(cursor.value);
  if (++count < 5) {
    cursor.continue();
  }
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم محدوده کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌های خود: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
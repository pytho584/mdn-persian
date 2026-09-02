---
title: IDBKeyRange
slug: Web/API/IDBKeyRange
page-type: web-api-interface
browser-compat: api.IDBKeyRange
---

{{APIRef("IndexedDB")}} {{AvailableInWorkers}}

رابط **`IDBKeyRange`** از [API IndexedDB](/en-US/docs/Web/API/IndexedDB_API) نشان‌دهندهٔ یک بازهٔ پیوسته بر روی یک نوع داده است که برای کلیدها استفاده می‌شود. رکوردها را می‌توان از اشیاء {{domxref("IDBObjectStore")}} و {{domxref("IDBIndex")}} با استفاده از کلیدها یا یک بازه از کلیدها بازیابی کرد. می‌توانید بازه را با استفاده از کران پایین و بالا محدود کنید. برای مثال، می‌توانید روی تمام مقادیر یک کلید در بازهٔ مقادیر A تا Z پیمایش کنید.

یک بازهٔ کلید می‌تواند یک مقدار واحد یا یک بازه با کران بالا و پایین یا نقاط انتهایی باشد. اگر بازهٔ کلید هم کران بالا و هم کران پایین داشته باشد، آن را _محدود_ می‌نامیم؛ اگر هیچ کرانی نداشته باشد، _نامحدود_ است. یک بازهٔ کلید محدود می‌تواند باز (نقاط انتهایی حذف شوند) یا بسته (نقاط انتهایی شامل شوند) باشد. برای بازیابی تمام کلیدهای درون یک بازهٔ مشخص، می‌توانید از ساختارهای کد زیر استفاده کنید:

| محدوده                       | کد                                   |
| --------------------------- | -------------------------------------- |
| تمام کلیدهای ≥ **x**            | `IDBKeyRange.lowerBound(x)`            |
| تمام کلیدهای > **x**            | `IDBKeyRange.lowerBound(x, true)`      |
| تمام کلیدهای ≤ **y**            | `IDBKeyRange.upperBound(y)`            |
| تمام کلیدهای < **y**            | `IDBKeyRange.upperBound(y, true)`      |
| تمام کلیدهای ≥ **x** && ≤ **y** | `IDBKeyRange.bound(x, y)`              |
| تمام کلیدهای > **x** &&< **y**  | `IDBKeyRange.bound(x, y, true, true)`  |
| تمام کلیدهای > **x** && ≤ **y** | `IDBKeyRange.bound(x, y, true, false)` |
| تمام کلیدهای ≥ **x** &&< **y**  | `IDBKeyRange.bound(x, y, false, true)` |
| کلید = **z**             | `IDBKeyRange.only(z)`                  |

یک کلید درون یک بازهٔ کلید است اگر شرایط زیر درست باشند:

- مقدار پایین بازهٔ کلید یکی از موارد زیر است:
  - `undefined`
  - کمتر از مقدار کلید
  - برابر با مقدار کلید اگر `lowerOpen` `false` باشد.
- مقدار بالای بازهٔ کلید یکی از موارد زیر است:
  - `undefined`
  - بزرگتر از مقدار کلید
  - برابر با مقدار کلید اگر `upperOpen` `false` باشد.

## ویژگی‌های نمونه

- {{domxref("IDBKeyRange.lower")}} {{ReadOnlyInline}}
  - : کران پایین بازهٔ کلید.
- {{domxref("IDBKeyRange.upper")}} {{ReadOnlyInline}}
  - : کران بالای بازهٔ کلید.
- {{domxref("IDBKeyRange.lowerOpen")}} {{ReadOnlyInline}}
  - : اگر مقدار کران پایین در بازهٔ کلید گنجانده شده باشد، `false` برمی‌گرداند.
- {{domxref("IDBKeyRange.upperOpen")}} {{ReadOnlyInline}}
  - : اگر مقدار کران بالا در بازهٔ کلید گنجانده شده باشد، `false` برمی‌گرداند.

## روش‌های ایستا

- {{domxref("IDBKeyRange.bound_static", "IDBKeyRange.bound()")}}
  - : یک بازهٔ کلید جدید با کران بالا و پایین ایجاد می‌کند.
- {{domxref("IDBKeyRange.only_static", "IDBKeyRange.only()")}}
  - : یک بازهٔ کلید جدید حاوی یک مقدار واحد ایجاد می‌کند.
- {{domxref("IDBKeyRange.lowerBound_static", "IDBKeyRange.lowerBound()")}}
  - : یک بازهٔ کلید جدید با فقط یک کران پایین ایجاد می‌کند.
- {{domxref("IDBKeyRange.upperBound_static", "IDBKeyRange.upperBound()")}}
  - : یک بازهٔ کلید کران بالا ایجاد می‌کند.

## روش‌های نمونه

- {{domxref("IDBKeyRange.includes()")}}
  - : یک مقدار بولی برمی‌گرداند که نشان می‌دهد آیا یک کلید مشخص درون بازهٔ کلید قرار دارد یا خیر.

## مثال‌ها

مثال زیر نحوه استفاده از یک بازهٔ کلید را نشان می‌دهد. در اینجا یک `keyRangeValue` را به عنوان بازه‌ای بین مقادیر `"A"` و `"F"` تعریف می‌کنیم. یک تراکنش (با استفاده از {{domxref("IDBTransaction")}}) و یک ذخیره‌گاه شیء باز می‌کنیم و یک مکان‌نما با {{domxref("IDBObjectStore.openCursor")}} باز می‌کنیم و `keyRangeValue` را به عنوان مقدار اختیاری بازهٔ کلید آن اعلام می‌کنیم. این بدان معناست که مکان‌نما فقط رکوردهایی را با کلیدهای درون آن بازه بازیابی می‌کند. این بازه شامل مقادیر `"A"` و `"F"` است، زیرا اعلام نکرده‌ایم که آنها کران‌های باز باشند. اگر از `IDBKeyRange.bound("A", "F", true, true);` استفاده می‌کردیم، آنگاه بازه شامل `"A"` و `"F"` نمی‌شد، فقط مقادیر بین آنها.

> [!NOTE]
> برای یک مثال کامل‌تر که به شما امکان آزمایش با بازهٔ کلید را می‌دهد، به مخزن [IDBKeyRange-example](https://github.com/mdn/dom-examples/tree/main/indexeddb-examples/idbkeyrange) ما نگاه کنید ([همچنین مثال زنده را مشاهده کنید](https://mdn.github.io/dom-examples/indexeddb-examples/idbkeyrange/).)

```js
function displayData() {
  const keyRangeValue = IDBKeyRange.bound("A", "F");

  const transaction = db.transaction(["fThings"], "readonly");
  const objectStore = transaction.objectStore("fThings");

  objectStore.openCursor(keyRangeValue).onsuccess = (event) => {
    const cursor = event.target.result;
    if (cursor) {
      const listItem = document.createElement("li");
      listItem.textContent = `${cursor.value.fThing}, ${cursor.value.fRating}`;
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
- بازیابی و ایجاد تغییرات در داده‌هایتان: {{domxref("IDBObjectStore")}}
- استفاده از مکان‌نماها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهدهٔ مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
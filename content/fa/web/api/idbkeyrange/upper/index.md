---
title: "IDBKeyRange: upper property"
short-title: upper
slug: Web/API/IDBKeyRange/upper
page-type: web-api-instance-property
browser-compat: api.IDBKeyRange.upper
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`upper`** در رابط {{domxref("IDBKeyRange")}}، کران بالای بازه کلید را برمی‌گرداند.

## مقدار

کران بالای بازه کلید (می‌تواند از هر نوعی باشد).

## مثال‌ها

مثال زیر نحوه استفاده از یک بازه کلید را نشان می‌دهد. در اینجا ما `keyRangeValue = IDBKeyRange.upperBound("F", "W", true, true);` را تعریف می‌کنیم — بازه‌ای که همه مقادیر بین "F" و "W" را شامل می‌شود اما خود این دو را شامل نمی‌شود، زیرا هر دو کران بالا و پایین به صورت باز (`true`) اعلام شده‌اند. ما یک تراکنش (با استفاده از {{domxref("IDBTransaction")}}) و یک object store باز می‌کنیم و یک Cursor را با {{domxref("IDBObjectStore.openCursor")}} باز می‌کنیم و `keyRangeValue` را به عنوان مقدار اختیاری بازه کلید آن تعیین می‌کنیم.

پس از تعریف بازه کلید، مقدار ویژگی `upper` آن را در کنسول ثبت می‌کنیم که باید به صورت "W" ظاهر شود.

> [!NOTE]
> برای یک مثال کامل‌تر که به شما امکان آزمایش با بازه کلید را می‌دهد، به مخزن [IDBKeyRange-example](https://github.com/mdn/dom-examples/tree/main/indexeddb-examples/idbkeyrange) مراجعه کنید ([نمونه زنده را نیز ببینید](https://mdn.github.io/dom-examples/indexeddb-examples/idbkeyrange/).)

```js
function displayData() {
  const keyRangeValue = IDBKeyRange.bound("F", "W", true, true);
  console.log(keyRangeValue.upper);

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
- تنظیم بازه‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌های خود: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
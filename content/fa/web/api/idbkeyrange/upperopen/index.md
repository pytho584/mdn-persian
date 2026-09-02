---
title: "IDBKeyRange: upperOpen property"
short-title: upperOpen
slug: Web/API/IDBKeyRange/upperOpen
page-type: web-api-instance-property
browser-compat: api.IDBKeyRange.upperOpen
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`upperOpen`** در رابط {{domxref("IDBKeyRange")}} یک مقدار بولی برمی‌گرداند که نشان می‌دهد آیا مقدار کران بالا در بازه کلید گنجانده شده است یا خیر.

## مقدار

یک مقدار بولی:

| مقدار | توضیح                                                    |
| ------- | ------------------------------------------------------- |
| `true` | مقدار کران بالا در بازه کلید گنجانده نشده است. |
| `false` | مقدار کران بالا در بازه کلید گنجانده شده است. |

## مثال‌ها

مثال زیر نحوه استفاده از یک بازه کلید را نشان می‌دهد. در اینجا ما `keyRangeValue = IDBKeyRange.upperBound("F", "W", true, true);` را تعریف می‌کنیم — بازه‌ای که همه مقادیر بین "F" و "W" را شامل می‌شود اما خودِ آن دو را شامل نمی‌شود — زیرا هر دو کران بالا و پایین به‌عنوان باز (`true`) اعلام شده‌اند. یک تراکنش (با استفاده از {{domxref("IDBTransaction")}}) و یک فروشگاه شیء باز می‌کنیم و یک نشانگر را با استفاده از {{domxref("IDBObjectStore.openCursor")}} باز می‌کنیم و `keyRangeValue` را به‌عنوان مقدار اختیاری بازه کلید آن تعیین می‌کنیم.

پس از تعریف بازه کلید، مقدار ویژگی `upperOpen` آن را در کنسول ثبت می‌کنیم که باید به‌صورت "true" ظاهر شود: کران بالا باز است و بنابراین در بازه گنجانده نخواهد شد.

> [!NOTE]
> برای مشاهده یک مثال کامل‌تر که به شما امکان آزمایش با بازه کلید را می‌دهد، به مخزن [IDBKeyRange-example](https://github.com/mdn/dom-examples/tree/main/indexeddb-examples/idbkeyrange) مراجعه کنید ([مشاهده مثال به‌صورت زنده](https://mdn.github.io/dom-examples/indexeddb-examples/idbkeyrange/).)

```js
function displayData() {
  const keyRangeValue = IDBKeyRange.bound("F", "W", true, true);
  console.log(keyRangeValue.upperOpen);

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
- تنظیم یک بازه از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی داده‌ها و ایجاد تغییرات در آن‌ها: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال به‌صورت زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
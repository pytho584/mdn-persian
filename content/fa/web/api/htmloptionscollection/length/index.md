---
title: "HTMLOptionsCollection: length property"
---

---
title: "HTMLOptionsCollection: length property"
short-title: length
slug: Web/API/HTMLOptionsCollection/length
page-type: web-api-instance-property
browser-compat: api.HTMLOptionsCollection.length
---

{{APIRef("DOM")}}

ویژگی **`length`** از رابط {{DOMxRef("HTMLOptionsCollection")}} تعداد عناصر {{htmlelement("option")}} موجود در مجموعه را بازمی‌گرداند. این ویژگی می‌تواند اندازهٔ مجموعه را بخواند یا آن را تنظیم کند.

هنگامی که `length` را روی مقداری کوچکتر از مقدار فعلی تنظیم کنید، مجموعهٔ گزینه‌ها کوتاه می‌شود؛ در غیر این صورت، عناصر جدید و خالی `<option>` به انتهای `<select>` اضافه می‌شوند.

## مقدار

یک عدد صحیح که تعداد آیتم‌های این `HTMLOptionsCollection` را نشان می‌دهد.

## مثال

```js
const optCollection = document.getElementById("fruits").options;
const origLength = optCollection.length;
optCollection.length += 50; // adds 50 blank options to the collection
optCollection.length = origLength; // truncates the list back to the original size
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{DOMxRef("HTMLOptionsCollection.add()")}}
- {{DOMxRef("HTMLOptionsCollection.remove()")}}
- {{DOMxRef("HTMLOptionsCollection.selectedIndex")}}
- {{domxref("HTMLSelectElement") }}
- {{domxref("HTMLOptGroupElement")}}
- {{domxref("HTMLCollection.length")}}
---
title: "HTMLOptionsCollection: selectedIndex property"
---

---
title: "HTMLOptionsCollection: selectedIndex property"
short-title: selectedIndex
slug: Web/API/HTMLOptionsCollection/selectedIndex
page-type: web-api-instance-property
browser-compat: api.HTMLOptionsCollection.selectedIndex
---

{{APIRef("HTML DOM")}}

ویژگی **`selectedIndex`** رابط {{DOMxRef("HTMLOptionsCollection")}}، شاخص عددی اولین عنصر {{HTMLElement("option")}} انتخاب‌شده است، در صورت وجود؛ و در صورتی که هیچ `<option>`ای انتخاب نشده باشد، مقدار آن `−1` است. تنظیم این ویژگی، گزینهٔ موجود در آن شاخص را انتخاب می‌کند و همهٔ گزینه‌های دیگر این مجموعه را از حالت انتخاب خارج می‌کند؛ همچنین تنظیم آن به `-1`، هر گزینهٔ انتخاب‌شدهٔ فعلی را از حالت انتخاب خارج می‌کند. این ویژگی دقیقاً معادل ویژگی {{domxref("HTMLSelectElement.selectedIndex", "selectedIndex")}} در {{domxref("HTMLSelectElement")}} ای است که مالک این مجموعه است.

## مقدار

یک عدد.

## مثال‌ها

```js
const optionColl = document.getElementById("select").options;
console.log(`selected option: ${optionColl.selectedIndex}`); // the index of the first selected option, or -1 if no option is selected
optionColl.selectedIndex = 0; // selects the first item
optionColl.selectedIndex = -1; // deselects any selected option
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{DOMxRef("HTMLOptionsCollection.length")}}
- {{DOMxRef("HTMLOptionsCollection.add()")}}
- {{DOMxRef("HTMLOptionsCollection.remove()")}}
- {{DOMxRef("HTMLOptionsCollection")}}
- {{DOMxRef("HTMLOptionElement")}}
- {{DOMxRef("HTMLOptGroupElement")}}
- {{DOMxRef("HTMLSelectElement")}}
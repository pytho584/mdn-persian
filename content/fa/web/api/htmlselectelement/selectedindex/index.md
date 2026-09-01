---
title: "HTMLSelectElement: selectedIndex property"
---

---
title: "HTMLSelectElement: selectedIndex property"
short-title: selectedIndex
slug: Web/API/HTMLSelectElement/selectedIndex
page-type: web-api-instance-property
browser-compat: api.HTMLSelectElement.selectedIndex
---

{{APIRef("HTML DOM")}}

ویژگی **`selectedIndex`** در رابط {{DOMxRef("HTMLSelectElement")}}، اندیس عددی نخستین عنصر {{HTMLElement("option")}}ِ انتخاب‌شده در یک عنصر {{HTMLElement("select")}} است؛ اگر هیچ گزینه‌ای انتخاب نشده باشد، مقدار `−1` برمی‌گرداند. تنظیم این ویژگی، گزینهٔ واقع در آن اندیس را انتخاب می‌کند و همهٔ گزینه‌های دیگر را از حالت انتخاب خارج می‌سازد؛ همچنین تنظیم آن به `-1`، هر گزینهٔ انتخاب‌شدهٔ فعلی را از حالت انتخاب خارج می‌کند.

## مقدار

یک عدد.

## مثال‌ها

### HTML

```html
<p id="p">selectedIndex: 0</p>

<select id="select">
  <option selected>Option A</option>
  <option>Option B</option>
  <option>Option C</option>
  <option>Option D</option>
  <option>Option E</option>
</select>
```

### JavaScript

```js
const selectElem = document.getElementById("select");
const pElem = document.getElementById("p");

// When a new <option> is selected
selectElem.addEventListener("change", () => {
  const index = selectElem.selectedIndex;
  // Add that data to the <p>
  pElem.textContent = `selectedIndex: ${index}`;
});
```

{{EmbedLiveSample("Examples", "200px", "120px")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{DOMxRef("HTMLSelectElement")}}
- {{DOMxRef("HTMLOptionElement")}}
- {{DOMxRef("HTMLOptionsCollection")}}
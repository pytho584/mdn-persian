---
title: "MutationRecord: oldValue property"
short-title: oldValue
slug: Web/API/MutationRecord/oldValue
page-type: web-api-instance-property
browser-compat: api.MutationRecord.oldValue

---

{{APIRef("DOM")}}

ویژگی فقط‌خواندنی **`oldValue`** در {{domxref("MutationRecord")}} حاوی داده‌های کاراکتری یا مقدار صفتِ یک گرهٔ مشاهده‌شده، پیش از تغییر آن است.

## مقدار

رشته‌ای که مقدار قدیمی صفتی را نشان می‌دهد که تغییر کرده است، در صورتی که:

- پارامتر `attributeOldValue` در {{domxref("MutationObserver.observe()")}} برابر با `true` باشد
- پارامتر `attributes` در {{domxref("MutationObserver.observe()")}} برابر با `true` باشد یا حذف شده باشد
- {{domxref("MutationRecord.type", "type")}} تغییر برابر با `attributes` باشد.

رشته‌ای که مقدار قدیمی یک گرهٔ {{domxref("CharacterData")}} را نشان می‌دهد که تغییر کرده است، در صورتی که:

- پارامتر `characterDataOldValue` در {{domxref("MutationObserver.observe()")}} برابر با `true` باشد
- پارامتر `characterData` در {{domxref("MutationObserver.observe()")}} برابر با `true` باشد یا حذف شده باشد
- {{domxref("MutationRecord.type", "type")}} تغییر برابر با `characterData` باشد.

در غیر این صورت، این ویژگی `null` است.

## مثال‌ها

### نمایش مقدار رنگ قدیمی

در مثال زیر، دکمه‌ای وجود دارد که رنگ یک `h1` را به یک رنگ تصادفی تازه تغییر می‌دهد. یک {{domxref("MutationObserver")}} برای مشاهدهٔ تغییرات صفت در گرهٔ هدف (`h1`) به کار می‌رود؛ وقتی تغییری تشخیص داده شود، observer تابع `logOldValue()` را فراخوانی می‌کند.

تابع `logOldValue()` آرایهٔ `mutationRecords` را دریافت می‌کند که حاوی اشیای {{domxref("MutationRecord")}} است. سپس ویژگی `oldValue` آن شیء، با رنگ مقدار قدیمی نمایش داده می‌شود.

#### HTML

```html
<h1 id="h1">Hi, Mom!</h1>
<button id="changeColorButton">Change color</button>
<p id="log"></p>
```

#### JavaScript

```js
const h1 = document.getElementById("h1");
const changeValueButton = document.getElementById("changeColorButton");
const log = document.getElementById("log");

changeColorButton.addEventListener("click", () => {
  // Random 6 character hexadecimal number to use as the hex color value
  const newColor = Math.floor(Math.random() * 16777215).toString(16);
  h1.style.color = `#${newColor}`;
});

function logOldValue(mutationRecordArray) {
  for (const record of mutationRecordArray) {
    log.textContent = `Old value: ${record.oldValue}`;
    log.style.cssText = record.oldValue;
  }
}

const observer = new MutationObserver(logOldValue);
observer.observe(h1, {
  attributes: true,
  attributeOldValue: true,
});
```

#### نتیجه

{{EmbedLiveSample("Show old color value", "", 200)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
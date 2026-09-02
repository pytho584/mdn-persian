---
title: "MutationRecord: attributeName property"
short-title: attributeName
slug: Web/API/MutationRecord/attributeName
page-type: web-api-instance-property
browser-compat: api.MutationRecord.attributeName
---

{{APIRef("DOM")}}

ویژگی فقط‌خواندنی **`attributeName`** از رابط {{domxref("MutationRecord")}} شامل نام ویژگی (attribute) تغییر یافته‌ای است که به گره‌ای متعلق است که توسط یک {{domxref("MutationObserver")}} مشاهده می‌شود.

## مقدار

اگر [`type`](/en-US/docs/Web/API/MutationRecord/type) رکورد برابر با `attributes` باشد، این یک رشته است که نام ویژگی جهش‌یافته هدف جهش را نشان می‌دهد.

اگر [`type`](/en-US/docs/Web/API/MutationRecord/type) رکورد برابر با `attributes` نباشد، مقدار آن `null` است.

## مثال‌ها

### دریافت نام آخرین ویژگی به‌روزرسانی‌شده

در مثال زیر چهار دکمه وجود دارد: دو دکمه ویژگی `style` عنصر `h1` را تغییر می‌دهند و دو دکمه ویژگی `class` عنصر `h1` را تغییر می‌دهند. اسکریپت از یک {{domxref("MutationObserver")}} برای شناسایی تغییرات استفاده می‌کند و متن زیر را به نام آخرین ویژگی تغییر یافته به‌روزرسانی می‌کند.

#### HTML

```html
<h1 class="blue" id="hiMom">Hi, Mom!</h1>

<button id="redButton">Set class to "red"</button>
<button id="blueButton">Set class to "blue"</button>
<button id="whiteButton">Set style to "color:white;"</button>
<button id="blackButton">Set style to "color:black;"</button>

<p id="log">Updated attribute name:</p>
```

#### CSS

```css
.red {
  background-color: red;
}

.blue {
  background-color: blue;
}
```

#### JavaScript

```js
const hiMom = document.querySelector("#hiMom");
const redButton = document.querySelector("#redButton");
const blueButton = document.querySelector("#blueButton ");
const whiteButton = document.querySelector("#whiteButton");
const blackButton = document.querySelector("#blackButton");
const log = document.querySelector("#log");

redButton.addEventListener("click", () => {
  hiMom.classList.add("red");
  hiMom.classList.remove("blue");
});

blueButton.addEventListener("click", () => {
  hiMom.classList.add("blue");
  hiMom.classList.remove("red");
});

whiteButton.addEventListener("click", () => {
  hiMom.style.color = "white";
});

blackButton.addEventListener("click", () => {
  hiMom.style.color = "black";
});

function logLastAttr(mutationRecordArray) {
  for (const record of mutationRecordArray) {
    if (record.type === "attributes") {
      log.textContent = `Updated attribute name: ${record.attributeName}`;
    }
  }
}

const observer = new MutationObserver(logLastAttr);
observer.observe(hiMom, { attributes: true });
```

#### نتیجه

{{EmbedLiveSample("Get last updated attribute name", "", 200)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
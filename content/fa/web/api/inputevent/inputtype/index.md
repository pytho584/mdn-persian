---
title: "InputEvent: inputType property"
short-title: inputType
slug: Web/API/InputEvent/inputType
page-type: web-api-instance-property
browser-compat: api.InputEvent.inputType
---

{{APIRef("UI Events")}}

خاصیت فقط-خواندنی **`inputType`** از رابط {{domxref("InputEvent")}} نوع تغییری که در محتوای قابل ویرایش ایجاد شده است را برمی‌گرداند. تغییرات ممکن شامل درج، حذف و قالب‌بندی متن است.

## مقدار

یک رشته حاوی نوع ورودی انجام شده. مقادیر احتمالی زیادی وجود دارد، مانند `insertText`، `deleteContentBackward`، `insertFromPaste` و `formatBold`. برای فهرست کامل انواع ورودی موجود، [بخش Attributes در مشخصات Input Events Level 2](https://w3c.github.io/input-events/#interface-InputEvent-Attributes) را ببینید.

## مثال‌ها

این مثال `inputType` را برای [رویدادهای input](/en-US/docs/Web/API/Element/input_event) روی یک {{htmlElement("div")}} قابل ویرایش ثبت می‌کند.

### HTML

```html
<p id="log">Input type:</p>
<div contenteditable="true" class="sample-text">
  <p>
    Some sample text. Try inserting line breaks, or deleting text in different
    ways, or pasting different content in.
  </p>
  <hr />
  <ul>
    <li>A sample</li>
    <li>bulleted</li>
    <li>list.</li>
  </ul>
  <p>Another paragraph.</p>
</div>
```

### CSS

```css
.sample-text {
  margin: 20px;
  padding: 20px;
  border: 2px dashed red;
}
```

### JavaScript

```js
const log = document.getElementById("log");
const editable = document.querySelector("div[contenteditable]");
editable.addEventListener("input", logInputType);

function logInputType(event) {
  log.textContent = `Input type: ${event.inputType}`;
}
```

### نتیجه

متن داخل `<div>` را ویرایش کنید و ببینید چه اتفاقی می‌افتد.

{{EmbedLiveSample("Examples", '100%', 500)}}

> [!NOTE]
> همچنین [مجموعه‌ی تست InputEvent از Masayuki Nakano](https://d-toybox.com/studio/lib/input_event_viewer.html) را برای یک مثال دقیق‌تر ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
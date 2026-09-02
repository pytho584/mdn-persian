---
title: "KeyboardEvent: charCode property"
short-title: charCode
slug: Web/API/KeyboardEvent/charCode
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.KeyboardEvent.charCode
---

{{APIRef("UI Events")}}{{Deprecated_Header}}

ویژگی فقط‌خواندنی **`charCode`** از رابط {{domxref("KeyboardEvent")}} مقدار یونیکد کلید کاراکتری را که در هنگام رویداد {{domxref("Element/keypress_event", "keypress")}} فشرده شده است، برمی‌گرداند.

> [!WARNING]
> از این ویژگی استفاده نکنید، زیرا منسوخ شده است. در عوض، مقدار یونیکد کاراکتر را با استفاده از ویژگی {{domxref("KeyboardEvent.key", "key")}} به دست آورید.

## مقدار

عددی که مقدار یونیکد کلید کاراکتری را که فشرده شده است نشان می‌دهد.

## مثال‌ها

### HTML

```html
<p>Type anything into the input box below to log a <code>charCode</code>.</p>
<input type="text" />
<p id="log"></p>
```

### JavaScript

```js
const input = document.querySelector("input");
const log = document.querySelector("#log");

input.addEventListener("keypress", (e) => {
  log.innerText = `Key pressed: ${String.fromCharCode(e.charCode)}\ncharCode: ${
    e.charCode
  }`;
});
```

### نتیجه

{{EmbedLiveSample("Examples")}}

## نکات

- در رویداد {{domxref("Element/keypress_event", "keypress")}}، مقدار یونیکد کلید فشرده‌شده در یکی از ویژگی‌های {{ domxref("KeyboardEvent.keyCode", "keyCode") }} یا `charCode` ذخیره می‌شود، اما هرگز در هر دو. اگر کلید فشرده‌شده یک کاراکتر تولید کند (مثلاً 'a')، `charCode` روی کد آن کاراکتر تنظیم می‌شود؛ `charCode` به حروف بزرگ و کوچک حساس است (به عبارت دیگر، `charCode` در نظر می‌گیرد که آیا کلید <kbd>shift</kbd> نگه داشته شده است یا خیر). در غیر این صورت، کد کلید فشرده‌شده در `keyCode` ذخیره می‌شود.
- `charCode` هرگز در رویدادهای {{domxref("Element/keydown_event", "keydown")}} و {{domxref("Element/keyup_event", "keyup")}} تنظیم نمی‌شود. در این موارد، به جای آن `keyCode` تنظیم می‌شود.
- برای دریافت کد کلید، صرف‌نظر از اینکه در `keyCode` یا `charCode` ذخیره شده باشد، ویژگی {{domxref("UIEvent/which", "which")}} را بپرسید.
- کاراکترهایی که از طریق یک {{glossary("Input method editor")}} وارد می‌شوند، از طریق `keyCode` یا `charCode` ثبت نمی‌شوند.
- برای فهرستی از مقادیر `charCode` مرتبط با کلیدهای خاص، [Displaying event object properties](/en-US/docs/Web/API/Document_Object_Model#displaying_event_object_properties) را اجرا و جدول HTML حاصل را مشاهده کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
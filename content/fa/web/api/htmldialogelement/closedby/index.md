---
title: "HTMLDialogElement: closedBy property"
short-title: closedBy
slug: Web/API/HTMLDialogElement/closedBy
page-type: web-api-instance-property
browser-compat: api.HTMLDialogElement.closedBy
---

{{ APIRef("HTML DOM") }}

ویژگی **`closedBy`** از رابط {{domxref("HTMLDialogElement")}} مشخص می‌کند که چه نوع اقداماتی از سوی کاربر می‌تواند برای بستن عنصر مربوطه {{htmlelement("dialog")}} استفاده شود. این ویژگی مقدار attribute [`closedby`](/en-US/docs/Web/HTML/Reference/Elements/dialog#closedby) دیالوگ را تنظیم یا بازمی‌گرداند.

## مقدار

یک رشته (string)؛ مقادیر ممکن عبارتند از:

- `any`
  - : دیالوگ می‌تواند با یک اقدام کاربری dismiss سبک (light dismiss)، یک اقدام کاربری خاص پلتفرم، یا یک مکانیسم تعریف‌شده توسط توسعه‌دهنده بسته شود.
- `closerequest`
  - : دیالوگ می‌تواند با یک اقدام کاربری خاص پلتفرم یا یک مکانیسم تعریف‌شده توسط توسعه‌دهنده بسته شود.
- `none`
  - : دیالوگ فقط با یک مکانیسم تعریف‌شده توسط توسعه‌دهنده قابل بستن است.

### رفتار پیش‌فرض

اگر attribute `closedby` وجود نداشته باشد یا نامعتبر باشد، به حالت **خودکار (Auto)** بازمی‌گردد. در حالت **خودکار**:

- زمانی که `<dialog>` با `showModal()` باز شود، طوری رفتار می‌کند که گویی `closedby="closerequest"` تنظیم شده است.
- زمانی که `<dialog>` با هر روش دیگری باز شود، طوری رفتار می‌کند که گویی `closedby="none"` تنظیم شده است.

## مثال‌ها

### استفادهٔ پایه از `closedBy`

```html
<dialog closedby="any">
  <p>
    Closable using the <kbd>Esc</kbd> key, or by clicking outside the dialog
    ("light dismiss").
  </p>
</dialog>
```

```html hidden
<pre id="log"></pre>
```

```js hidden
const logElement = document.getElementById("log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

```js
const dialog = document.querySelector("dialog");
dialog.showModal();
log(`closedBy: ${dialog.closedBy}`);
```

### نتیجه

{{ EmbedLiveSample('Basic `closedBy` usage', '100%', '250px') }}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- عنصر HTML {{htmlelement("dialog")}}
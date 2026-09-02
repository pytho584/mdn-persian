---
title: "HTMLTextAreaElement: select event"
---

---
title: "HTMLTextAreaElement: select event"
short-title: select
slug: Web/API/HTMLTextAreaElement/select_event
page-type: web-api-event
browser-compat: api.HTMLTextAreaElement.select_event
---

{{APIRef("Selection API")}}

رویداد **`select`** زمانی رخ می‌دهد که متنی انتخاب شده باشد.

## Syntax

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت رویداد را تنظیم نمایید.

```js-nolint
addEventListener("select", (event) => { })

onselect = (event) => { }
```

## Event type

یک {{domxref("Event")}} عمومی.

## Examples

### ثبت انتخاب

```html
<textarea>Try selecting some text in this element.</textarea>
<p id="log"></p>
```

```js
function logSelection(event) {
  const log = document.getElementById("log");
  const selection = event.target.value.substring(
    event.target.selectionStart,
    event.target.selectionEnd,
  );
  log.textContent = `You selected: ${selection}`;
}

const textarea = document.querySelector("textarea");
textarea.addEventListener("select", logSelection);
```

{{EmbedLiveSample("Selection_logger")}}

### معادل onselect

همچنین می‌توانید مدیریت رویداد را با استفاده از ویژگی `onselect` تنظیم کنید:

```js
textarea.onselect = logSelection;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLTextAreaElement.select()")}}
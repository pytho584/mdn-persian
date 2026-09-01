---
title: "HTMLInputElement: select event"
short-title: select
slug: Web/API/HTMLInputElement/select_event
page-type: web-api-event
browser-compat: api.HTMLInputElement.select_event
---

{{APIRef("HTML DOM")}}

رویداد **`select`** زمانی فعال می‌شود که مقداری متن انتخاب شده باشد.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی event handler تنظیم کنید.

```js-nolint
addEventListener("select", (event) => { })

onselect = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

### ثبت‌کننده انتخاب (Selection logger)

```html
<input value="Try selecting some text in this element." />
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

const input = document.querySelector("input");
input.addEventListener("select", logSelection);
```

{{EmbedLiveSample("Selection_logger")}}

### معادل onselect

همچنین می‌توانید event handler را با استفاده از ویژگی `onselect` تنظیم کنید:

```js
input.onselect = logSelection;
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}
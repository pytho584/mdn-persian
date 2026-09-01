---
title: "HTMLFormElement: submit event"
short-title: submit
slug: Web/API/HTMLFormElement/submit_event
page-type: web-api-event
browser-compat: api.HTMLFormElement.submit_event
---

{{APIRef("HTML DOM")}}

رویداد **`submit`** زمانی رخ می‌دهد که یک {{HtmlElement("form")}} ارسال می‌شود.

توجه داشته باشید که رویداد `submit` روی خود عنصر `<form>` رخ می‌دهد، نه روی هیچ {{HtmlElement("button")}} یا `{{HtmlElement('input/submit', '&lt;input type="submit"&gt;')}}` داخل آن. با این حال، {{domxref("SubmitEvent")}} که برای نشان دادن فعال شدن اقدام ارسال فرم ارسال می‌شود، شامل یک ویژگی {{domxref("SubmitEvent.submitter", "submitter")}} است که دکمه‌ای است که برای شروع درخواست ارسال فراخوانی شده است.

رویداد `submit` در موارد زیر رخ می‌دهد:

- کاربر روی یک {{Glossary("submit button", "دکمه ارسال")}} کلیک کند،
- کاربر در حال ویرایش یک فیلد (مانند {{HtmlElement('input/text', '&lt;input type="text"&gt;')}}) در یک فرم، کلید <kbd>Enter</kbd> را فشار دهد،
- یک اسکریپت متد {{domxref("HTMLFormElement.requestSubmit()", "form.requestSubmit()")}} را فراخوانی کند.

با این حال، رویداد _به_ فرم ارسال _نمی‌شود_ زمانی که یک اسکریپت مستقیماً متد {{domxref("HTMLFormElement.submit()", "form.submit()")}} را فراخوانی کند.

> [!NOTE]
> تلاش برای ارسال فرمی که از [اعتبارسنجی](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation) عبور نمی‌کند، باعث رخ دادن رویداد {{domxref("HTMLInputElement/invalid_event", "invalid")}} می‌شود. در این حالت، اعتبارسنجی از ارسال فرم جلوگیری می‌کند و بنابراین رویداد `submit` وجود نخواهد داشت.

## نحو

از نام رویداد در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("submit", (event) => { })

onsubmit = (event) => { }
```

## نوع رویداد

یک {{domxref("SubmitEvent")}}. از {{domxref("Event")}} ارث‌بری می‌کند.

{{InheritanceDiagram("SubmitEvent")}}

## نمونه‌ها

این مثال از {{domxref("EventTarget.addEventListener()")}} برای گوش دادن به رویداد submit فرم استفاده می‌کند و {{domxref("Event.timeStamp")}} جاری را هر بار که این رویداد رخ می‌دهد ثبت می‌کند، سپس اقدام پیش‌فرض ارسال فرم را جلوگیری می‌کند.

### HTML

```html
<form id="form">
  <label>Test field: <input type="text" /></label>
  <br /><br />
  <button type="submit">Submit form</button>
</form>
<p id="log"></p>
```

### JavaScript

```js
const form = document.getElementById("form");
const log = document.getElementById("log");

function logSubmit(event) {
  log.textContent = `Form Submitted! Timestamp: ${event.timeStamp}`;
  event.preventDefault();
}

form.addEventListener("submit", logSubmit);
```

### نتیجه

{{EmbedLiveSample("Examples", "", "", "", "", "", "", "allow-forms")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- عنصر HTML {{HtmlElement("form")}}
- رویداد مرتبط: {{domxref("HTMLInputElement/invalid_event", "invalid")}}
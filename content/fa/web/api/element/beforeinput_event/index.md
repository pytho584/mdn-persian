---
title: "Element: beforeinput event"
---

---
title: "Element: beforeinput event"
short-title: beforeinput
slug: Web/API/Element/beforeinput_event
page-type: web-api-event
browser-compat: api.Element.beforeinput_event
---

{{APIRef("UI Events")}}

رویداد **`beforeinput`** در DOM زمانی فعال می‌شود که مقدار یک عنصر {{HTMLElement("input")}} یا {{HTMLElement("textarea")}} در آستانه تغییر باشد. اما بر خلاف رویداد {{domxref("Element/input_event", "input")}}، روی عنصر {{HTMLElement("select")}} فعال نمی‌شود. این رویداد همچنین برای عناصری که {{domxref("HTMLElement.contentEditable", "contenteditable")}} در آن‌ها فعال است و همچنین برای هر عنصری وقتی {{domxref("Document.designMode", "designMode")}} روشن باشد، اعمال می‌شود.

این امکان را به برنامه‌های وب می‌دهد تا قبل از اینکه مرورگر درخت DOM را تغییر دهد، رفتار ویرایش متن را بازنویسی کنند و کنترل بیشتری روی رویدادهای ورودی برای بهبود کارایی فراهم می‌کند.

در مورد `contenteditable` و `designMode`، هدف رویداد **میزبان ویرایش** است. اگر این ویژگی‌ها روی چند عنصر اعمال شوند، میزبان ویرایش نزدیک‌ترین عنصر جد است که والد آن قابل ویرایش نیست.

> [!NOTE]
> هر تغییری توسط کاربر منجر به فعال شدن `beforeinput` نمی‌شود. همچنین ممکن است رویداد فعال شود اما قابل لغو (cancelable) نباشد. این اتفاق ممکن است زمانی رخ دهد که تغییر توسط تکمیل خودکار (autocomplete)، پذیرش اصلاحیه از غلط‌یاب املایی، تکمیل خودکار مدیریت رمز عبور، توسط {{Glossary("Input method editor", "IME")}} یا به روش‌های دیگر انجام شود. جزئیات بسته به مرورگر و سیستم‌عامل متفاوت است. برای بازنویسی رفتار ویرایش در همه شرایط، کد باید رویداد `input` را مدیریت کند و احتمالاً تغییراتی را که توسط کنترل‌کننده `beforeinput` مدیریت نشده‌اند، بازگرداند. به باگ‌های [1673558](https://bugzil.la/1673558) و [1763669](https://bugzil.la/1763669) مراجعه کنید.

## سینتکس

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("beforeinput", (event) => { })

onbeforeinput = (event) => { }
```

## نوع رویداد

یک {{domxref("InputEvent")}}. به ارث‌برده شده از {{domxref("UIEvent")}}.

{{InheritanceDiagram("InputEvent")}}

## مثال‌ها

### تشخیص ویژگی

تابع زیر مقدار `true` را برمی‌گرداند اگر `beforeinput` و بنابراین `getTargetRanges` پشتیبانی شود.

```js
function isBeforeInputEventAvailable() {
  return (
    window.InputEvent &&
    typeof InputEvent.prototype.getTargetRanges === "function"
  );
}
```

### ثبت‌کننده ساده

این مثال مقدار فعلی عنصر را، بلافاصله قبل از جایگزینی آن مقدار با مقدار جدید اعمال‌شده روی عنصر {{HtmlElement("input")}}، ثبت می‌کند.

#### HTML

```html
<input placeholder="Enter some text" name="name" />
<p id="values"></p>
```

#### JavaScript

```js
const input = document.querySelector("input");
const log = document.getElementById("values");

input.addEventListener("beforeinput", updateValue);

function updateValue(e) {
  log.textContent = e.target.value;
}
```

#### نتیجه

{{EmbedLiveSample("Simple_logger")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویداد مرتبط: {{domxref("Element/input_event", "input")}}
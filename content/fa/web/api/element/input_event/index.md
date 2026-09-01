---
title: "Element: input event"
short-title: input
slug: Web/API/Element/input_event
page-type: web-api-event
browser-compat: api.Element.input_event
---

{{APIRef("UI Events")}}

رویداد **`input`** زمانی رخ می‌دهد که مقدار (`value`) یک عنصر {{HTMLElement("input")}}، {{HTMLElement("select")}} یا {{HTMLElement("textarea")}} در نتیجهٔ مستقیم یک اقدام کاربر (مانند تایپ کردن در یک جعبه متن یا علامت زدن یک چک‌باکس) تغییر کند.

این رویداد همچنین برای عناصری که {{domxref("HTMLElement.contentEditable", "contenteditable")}} در آن‌ها فعال است و نیز هر عنصری وقتی {{domxref("Document.designMode", "designMode")}} روشن باشد اعمال می‌شود. در مورد `contenteditable` و `designMode`، هدف رویداد، _میزبان ویرایش_ (editing host) است. اگر این ویژگی‌ها برای چندین عنصر اعمال شوند، میزبان ویرایش، نزدیک‌ترین عنصر بالادستی (ancestor) است که والد آن قابل ویرایش نباشد.

برای عناصر `<input>` با `type=checkbox` یا `type=radio`، رویداد `input` باید هر بار که کاربر کنترل را تغییر می‌دهد، مطابق [مشخصات HTML Living Standard](https://html.spec.whatwg.org/multipage/input.html#the-input-element:event-input-2) رخ دهد. با این حال، از نظر تاریخی همیشه این‌طور نبوده است. سازگاری را بررسی کنید، یا برای این نوع عناصر به جای آن از رویداد {{domxref("HTMLElement/change_event", "change")}} استفاده کنید.

برای عناصر {{htmlelement("textarea")}} و {{htmlelement("input")}} که ورودی متنی می‌پذیرند (`type=text`، `type=tel` و غیره)، رابط رویداد {{DOMxRef("InputEvent")}} است؛ برای بقیه، رابط رویداد {{DOMxRef("Event")}} است.

رویداد `input` هر بار که مقدار (`value`) عنصر تغییر کند، رخ می‌دهد. این برخلاف رویداد {{domxref("HTMLElement/change_event", "change")}} است که فقط زمانی رخ می‌دهد که مقدار ثبت (commit) شود، مثلاً با فشردن کلید Enter یا انتخاب یک مقدار از فهرست گزینه‌ها. توجه داشته باشید که وقتی JavaScript به‌صورت برنامه‌نویسی‌شده مقدار (`value`) یک عنصر را تغییر دهد، رویداد `input` رخ نمی‌دهد.

## نحو (Syntax)

برای استفاده، نام رویداد را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به کار ببرید یا یک ویژگی کنترل‌کننده رویداد (event handler property) تنظیم کنید.

```js-nolint
addEventListener("input", (event) => { })

oninput = (event) => { }
```

## نوع رویداد

یک {{domxref("InputEvent")}}. از {{domxref("UIEvent")}} به ارث می‌برد.

{{InheritanceDiagram("InputEvent")}}

## مثال‌ها

این مثال هر بار که مقدار عنصر {{HtmlElement("input")}} را تغییر دهید، مقدار جدید را ثبت (log) می‌کند.

### HTML

```html
<input placeholder="Enter some text" name="name" />
<p id="values"></p>
```

### JavaScript

```js
const input = document.querySelector("input");
const log = document.getElementById("values");

input.addEventListener("input", updateValue);

function updateValue(e) {
  log.textContent = e.target.value;
}
```

### نتیجه

{{EmbedLiveSample("Examples")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویدادهای مرتبط
  - {{domxref("Element/beforeinput_event", "beforeinput")}}
  - {{domxref("HTMLElement/change_event", "change")}}
  - {{domxref("HTMLInputElement/invalid_event", "invalid")}}
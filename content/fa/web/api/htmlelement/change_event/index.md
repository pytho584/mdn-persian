---
title: "HTMLElement: change event"
short-title: change
slug: Web/API/HTMLElement/change_event
page-type: web-api-event
browser-compat: api.HTMLElement.change_event
---

{{APIRef("HTML DOM")}}

رویداد `change` برای عناصر {{HTMLElement("input")}}، {{HTMLElement("select")}} و {{HTMLElement("textarea")}} هنگامی که کاربر مقدار عنصر را تغییر می‌دهد، فعال می‌شود. برخلاف رویداد {{domxref("Element/input_event", "input")}}، رویداد `change` لزوماً برای هر تغییر در `value` عنصر فعال نمی‌شود.

بسته به نوع عنصر در حال تغییر و نحوه تعامل کاربر با آن، رویداد `change` در لحظه‌های متفاوتی فعال می‌شود:

- هنگامی که یک عنصر `{{HTMLElement('input/checkbox', '&lt;input type="checkbox"&gt;')}}` علامت‌دار یا بی‌علامت می‌شود (با کلیک یا استفاده از صفحه‌کلید)؛
- هنگامی که یک عنصر `{{HTMLElement('input/radio', '&lt;input type="radio"&gt;')}}` علامت‌دار می‌شود (اما نه زمانی که بی‌علامت می‌شود)؛
- هنگامی که کاربر تغییر را به صورت صریح اعمال می‌کند (مثلاً با انتخاب یک مقدار از منوی کشویی {{HTMLElement("select")}} با کلیک ماوس، انتخاب یک تاریخ از انتخاب‌گر تاریخ برای `{{HTMLElement('input/date', '&lt;input type="date"&gt;')}}`، انتخاب یک فایل در انتخاب‌گر فایل برای `{{HTMLElement('input/file', '&lt;input type="file"&gt;')}}` و غیره)؛
- هنگامی که عنصر پس از تغییر مقدار خود، فوکوس را از دست می‌دهد: برای عناصری که تعامل کاربر تایپ کردن است نه انتخاب کردن، مانند {{HTMLElement("textarea")}} یا انواع `{{HTMLElement('input/text', 'text')}}`، `{{HTMLElement('input/search', 'search')}}`، `{{HTMLElement('input/url', 'url')}}`، `{{HTMLElement('input/tel', 'tel')}}`، `{{HTMLElement('input/email', 'email')}}` یا `{{HTMLElement('input/password', 'password')}}` از عنصر {{HTMLElement('input')}}.

مشخصات HTML [انواع `<input>` که باید رویداد `change` را فعال کنند](https://html.spec.whatwg.org/multipage/forms.html#concept-input-apply) فهرست کرده است.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("change", (event) => { })

onchange = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## نمونه‌ها

### عنصر `<select>`

#### HTML

```html
<label>
  Choose an ice cream flavor:
  <select class="ice-cream" name="ice-cream">
    <option value="">Select One …</option>
    <option value="chocolate">Chocolate</option>
    <option value="sardine">Sardine</option>
    <option value="vanilla">Vanilla</option>
  </select>
</label>

<div class="result"></div>
```

```css hidden
body {
  display: grid;
  grid-template-areas: "select result";
}

select {
  grid-area: select;
}

.result {
  grid-area: result;
}
```

#### JavaScript

```js
const selectElement = document.querySelector(".ice-cream");
const result = document.querySelector(".result");

selectElement.addEventListener("change", (event) => {
  result.textContent = `You like ${event.target.value}`;
});
```

#### نتیجه

{{ EmbedLiveSample('select_element', '100%', '75px') }}

### عنصر ورودی متنی

برای برخی عناصر، از جمله `<input type="text">`، رویداد `change` تا زمانی که کنترل فوکوس خود را از دست ندهد فعال نمی‌شود. سعی کنید چیزی در فیلد زیر وارد کنید، سپس روی جای دیگری کلیک کنید تا رویداد فعال شود.

#### HTML

```html
<input placeholder="Enter some text" name="name" />
<p id="log"></p>
```

#### JavaScript

```js
const input = document.querySelector("input");
const log = document.getElementById("log");

input.addEventListener("change", updateValue);

function updateValue(e) {
  log.textContent = e.target.value;
}
```

#### نتیجه

{{ EmbedLiveSample('Text_input_element', '100%', '90px') }}

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

مرورگرهای مختلف همیشه در مورد اینکه آیا رویداد `change` باید برای انواع خاصی از تعامل فعال شود یا خیر، توافق ندارند. به عنوان مثال، پیمایش صفحه‌کلید در عناصر {{HTMLElement("select")}} قبلاً هرگز رویداد `change` را در Gecko فعال نمی‌کرد تا زمانی که کاربر Enter را فشار دهد یا فوکوس را از `<select>` دور کند (به [باگ 126379 فایرفاکس](https://bugzil.la/126379) مراجعه کنید). از فایرفاکس 63 (Quantum) به بعد، این رفتار در همه مرورگرهای اصلی یکسان شده است.
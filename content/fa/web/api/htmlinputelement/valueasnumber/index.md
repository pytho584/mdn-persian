---
title: "HTMLInputElement: valueAsNumber property"
short-title: valueAsNumber
slug: Web/API/HTMLInputElement/valueAsNumber
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.valueAsNumber
---

{{ APIRef("HTML DOM") }}

ویژگی **`valueAsNumber`** از رابط {{DOMxRef("HTMLInputElement")}} مقدار فعلی عنصر {{htmlelement("input")}} را به صورت یک عدد یا `NaN` در صورتی که تبدیل به مقدار عددی ممکن نباشد، نمایش می‌دهد.

این ویژگی را می‌توان مستقیماً نیز تنظیم کرد، مثلاً برای تعیین یک مقدار عددی پیش‌فرض بر اساس شرطی خاص.

## مقدار

یک عدد که مقدار عنصر را نشان می‌دهد یا `NaN` اگر تبدیل عددی غیرممکن باشد.

## مثال‌ها

### دریافت یک مقدار عددی

در این مثال، لاگ مقدار فعلی ورودی {{HTMLElement("input/number", "number")}} را هنگام تغییر نمایش می‌دهد.

#### HTML

ما یک {{htmlelement("input")}} از نوع `number` و یک {{htmlelement("label")}} مرتبط به همراه یک ظرف {{htmlelement("pre")}} برای خروجی قرار می‌دهیم.

```html
<label for="number">یک عدد بین ۱ تا ۱۰ انتخاب کنید:</label>

<input name="number" id="number" min="1" max="10" type="number" />

<pre id="log"></pre>
```

#### JavaScript

متن داخلی ({{domxref("HTMLElement.innerText", "innerText")}}) عنصر `<pre>` هر بار که رویداد {{domxref("HTMLElement/change_event", "change")}} رخ می‌دهد، به مقدار فعلی `<input>` به‌روزرسانی می‌شود.

```js
const logElement = document.getElementById("log");
const inputElement = document.getElementById("number");

inputElement.addEventListener("change", () => {
  logElement.innerText = `عدد: ${inputElement.valueAsNumber}`;
});
```

```css hidden
#log {
  height: 20px;
  padding: 0.5rem;
  background-color: #ededed;
}
```

#### نتایج

{{EmbedLiveSample("Retrieving a number value", "", 100)}}

اگر عدد را در ویجت پاک کنید، نتیجه `NaN` خواهد بود.

### دریافت یک مقدار تاریخ به صورت عدد

این مثال ویژگی `valueAsNumber` یک `<input>` از نوع {{HTMLElement("input/datetime-local", "datetime-local")}} را نشان می‌دهد.

#### HTML

ما یک `<input>` از نوع `datetime-local` قرار می‌دهیم:

```html
<label for="date">یک تاریخ و زمان انتخاب کنید:</label>

<input name="date" id="date" type="datetime-local" />

<pre id="log"></pre>
```

#### JavaScript

هنگامی که هیچ تاریخ یا زمانی انتخاب نشده باشد، رشته خالی به `NaN` تبدیل می‌شود. هر بار که انتخابی انجام شود، یک رویداد {{domxref("HTMLElement/change_event", "change")}} رخ می‌دهد و محتوای `<pre>` را به‌روزرسانی می‌کند که {{DOMXref("HTMLInputElement.value")}} کنترل فرم را در مقایسه با آن مقدار به صورت عدد نشان می‌دهد.

```js
const logElement = document.getElementById("log");
const inputElement = document.getElementById("date");

logElement.innerText = `مقدار اولیه: ${inputElement.valueAsNumber}`;

inputElement.addEventListener("change", () => {
  const d = new Date(inputElement.valueAsNumber);
  logElement.innerText = `${inputElement.value} به ${inputElement.valueAsNumber} تبدیل می‌شود، \nکه برابر با ${d.toDateString()} در ساعت ${d.toTimeString()} است.`;
});
```

```css hidden
#log {
  height: 20px;
  padding: 0.5rem;
  background-color: #ededed;
}
```

#### نتایج

{{EmbedLiveSample("Retrieving a date value as a number", "", 100)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("input")}}
- {{DOMXref("HTMLInputElement.value")}}
- {{DOMXref("HTMLInputElement.valueAsDate")}}
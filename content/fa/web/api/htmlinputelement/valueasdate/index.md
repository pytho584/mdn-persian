---
title: "HTMLInputElement: valueAsDate property"
short-title: valueAsDate
slug: Web/API/HTMLInputElement/valueAsDate
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.valueAsDate
---

{{ APIRef("HTML DOM") }}

ویژگی **`valueAsDate`** از رابط {{DOMxRef("HTMLInputElement")}}، مقدار فعلی عنصر {{htmlelement("input")}} را به صورت یک {{jsxref("Date")}} نمایش می‌دهد، یا اگر تبدیل امکان‌پذیر نباشد، مقدار `null` را برمی‌گرداند.

این ویژگی را می‌توان به‌طور مستقیم نیز تنظیم کرد، مثلاً برای تعیین یک تاریخ پیش‌فرض بر اساس یک شرط. اگر مقدار ارائه‌شده نه `null` باشد و نه یک شیء `Date`، یک {{jsxref("TypeError")}} پرتاب می‌شود. اگر مقدار ارائه‌شده `null` یا یک [تاریخ نامعتبر](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date#the_epoch_timestamps_and_invalid_date) باشد، مقدار ورودی به رشته خالی تنظیم می‌شود.

این ویژگی همیشه وقتی که روی یک ورودی که بر پایه تاریخ یا زمان نیست فراخوانی شود، `null` برمی‌گرداند. هنگام تنظیم این ویژگی روی چنین ورودی، یک `InvalidStateError` از نوع {{domxref("DOMException")}} پرتاب می‌شود.

## مقدار

یک شیء {{jsxref("Date")}} یا اگر تبدیل غیرممکن باشد، `null`. تاریخی که برگردانده می‌شود همیشه باید به‌عنوان زمان UTC تفسیر شود — مثلاً با استفاده از روش‌هایی مانند `getUTCDate()` به‌جای `getDate()`. اگر دقت نکنید، نتیجه ممکن است یک روز اختلاف داشته باشد — مثلاً اگر کاربر در یک منطقه زمانی با آفست منفی UTC (مثلاً ایالات متحده) زندگی کند، تفسیر تاریخ به‌عنوان تاریخ محلی، روز قبل از آنچه کاربر انتخاب کرده را نشان می‌دهد.

انواع ورودی [`month`](/en-US/docs/Web/HTML/Reference/Elements/input/month)، [`date`](/en-US/docs/Web/HTML/Reference/Elements/input/date) و [`week`](/en-US/docs/Web/HTML/Reference/Elements/input/week) یک تاریخ UTC برمی‌گردانند که نشان‌دهنده اولین لحظه از بازه زمانی واردشده است — یعنی همیشه نیمه‌شب به وقت UTC هستند. برای `month`، تاریخ اولین روز ماه است. برای `week`، تاریخ دوشنبه همان هفته است. نوع ورودی [`time`](/en-US/docs/Web/HTML/Reference/Elements/input/time) همیشه تاریخ را `1970-01-01` تنظیم می‌کند.

نوع ورودی [`datetime-local`](/en-US/docs/Web/HTML/Reference/Elements/input/datetime-local) از ویژگی `valueAsDate` پشتیبانی نمی‌کند، زیرا این نوع ورودی یک تاریخ و زمان را در منطقه زمانی محلی (یک [زمان ساعت‌دیواری](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Temporal/PlainDateTime)) نشان می‌دهد، در حالی که اشیاء `Date` یک نقطه مطلق در زمان را نشان می‌دهند. با این حال، برخی مرورگرها ممکن است یک پیاده‌سازی غیراستاندارد ارائه دهند. [WHATWG در حال کار روی یکپارچه‌سازی](https://github.com/whatwg/html/issues/10882) API مربوط به {{jsxref("Temporal")}} با ورودی‌های تاریخ/زمان برای پوشش این مورد استفاده است.

## مثال‌ها

### دریافت مقدار تاریخ

این مثال دسترسی به ویژگی `valueAsDate` را روی یک `<input>` از نوع {{HTMLElement("input/week", "week")}} نشان می‌دهد.

#### HTML

ما یک `<input>` از نوع `week` قرار می‌دهیم:

```html
<label for="date">یک تاریخ و زمان انتخاب کنید:</label>

<input name="date" id="date" type="week" />

<pre id="log"></pre>
```

#### JavaScript

وقتی هیچ تاریخ یا زمانی انتخاب نشده باشد، ورودی خالی به `null` تبدیل می‌شود. هر بار که انتخابی انجام شود، یک رویداد {{domxref("HTMLElement/change_event", "change")}} فعال می‌شود و محتوای `<pre>` به‌روزرسانی می‌شود که {{DOMXref("HTMLInputElement.value")}} کنترل فرم را در مقایسه با آن مقدار به‌صورت تاریخ نشان می‌دهد.

```js
const logElement = document.getElementById("log");
const inputElement = document.getElementById("date");

logElement.innerText = `مقدار اولیه: ${inputElement.valueAsDate}`;

inputElement.addEventListener("change", () => {
  logElement.innerText = `${inputElement.value} به ${inputElement.valueAsDate} تبدیل می‌شود`;
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

{{EmbedLiveSample("Retrieving a date value", "", 100)}}

### استفاده از روش‌های Date

این مثال استفاده مستقیم از روش‌های {{jsxref("Date")}} روی ویژگی `valueAsDate` یک `<input>` از نوع {{HTMLElement("input/date", "date")}} را نشان می‌دهد.

#### HTML

ما یک `<input>` از نوع `date` قرار می‌دهیم:

```html
<label for="date2">یک تاریخ انتخاب کنید:</label>

<input name="date2" id="date2" type="date" />

<pre id="log"></pre>
```

#### JavaScript

وقتی هیچ تاریخی انتخاب نشده باشد، رشته خالی به `null` تبدیل می‌شود. هر بار که انتخابی انجام شود، یک رویداد {{domxref("HTMLElement/change_event", "change")}} فعال می‌شود. سپس لاگ را با تاریخ انتخاب‌شده پر می‌کنیم که با استفاده از روش {{jsxref("Date.prototype.toLocaleDateString()", "toLocaleDateString()")}} شیء `Date` قالب‌بندی شده است.

```js
const logElement = document.getElementById("log");
const inputElement = document.getElementById("date2");
const options = {
  weekday: "long",
  year: "numeric",
  month: "long",
  day: "numeric",
};

logElement.innerText = `مقدار اولیه: ${inputElement.valueAsDate}`;

inputElement.addEventListener("change", () => {
  if (inputElement.valueAsDate !== null) {
    logElement.innerText = `شما انتخاب کردید ${inputElement.valueAsDate.toLocaleDateString("en-US", options)}`;
  } else {
    logElement.innerText = `${inputElement.value} به ${inputElement.valueAsDate} تبدیل می‌شود`;
  }
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

{{EmbedLiveSample("Using Date methods", "", 100)}}

تاریخ ممکن است به دلیل منطقه زمانی محلی شما یک روز اختلاف داشته باشد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("input")}}
- {{DOMXref("HTMLInputElement.value")}}
- {{DOMXref("HTMLInputElement.valueAsNumber")}}
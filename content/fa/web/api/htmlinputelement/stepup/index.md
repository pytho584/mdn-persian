---
title: "HTMLInputElement: stepUp() method"
short-title: stepUp()
slug: Web/API/HTMLInputElement/stepUp
page-type: web-api-instance-method
browser-compat: api.HTMLInputElement.stepUp
---

{{APIRef("HTML DOM")}}

متد **`HTMLInputElement.stepUp()`** مقدار یک عنصر {{HTMLElement("input")}} از نوع عددی را به اندازه‌ی مقدار ویژگی [`step`](/en-US/docs/Web/HTML/Reference/Attributes/step) یا در صورت عدم تعیین صریح ویژگی `step`، به اندازه‌ی مقدار پیش‌فرض `step` افزایش می‌دهد. این متد هنگام فراخوانی، مقدار [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value) را به اندازه‌ی ([`step`](/en-US/docs/Web/HTML/Reference/Elements/input#step) \* n) افزایش می‌دهد، که در آن `n` در صورت عدم مشخص‌شدن پیش‌فرض `1` است و [`step`](/en-US/docs/Web/HTML/Reference/Attributes/step) در صورت عدم مشخص‌شدن، مقدار پیش‌فرض خود را دارد.

<table class="no-markdown">
  <thead>
    <tr>
      <th>نوع ورودی</th>
      <th>مقدار گام پیش‌فرض</th>
      <th>نمونه اعلام گام</th>
    </tr>
    <tr>
      <td>{{HTMLElement("input/date", "date")}}</td>
      <td><code>1</code> (روز)</td>
      <td>
        افزایش‌های ۷ روزه (یک هفته):<br />
        <code>&#x3C;input type="date" min="2019-12-25" step="7"></code>
      </td>
    </tr>
    <tr>
      <td>{{HTMLElement("input/month", "month")}}</td>
      <td><code>1</code> (ماه)</td>
      <td>
        افزایش‌های ۱۲ ماهه (یک سال):<br />
        <code>&#x3C;input type="month" min="2019-12" step="12"></code>
      </td>
    </tr>
    <tr>
      <td>{{HTMLElement("input/week", "week")}}</td>
      <td><code>1</code> (هفته)</td>
      <td>
        افزایش‌های دو هفته‌ای:<br />
        <code>&#x3C;input type="week" min="2019-W23" step="2"></code>
      </td>
    </tr>
    <tr>
      <td>{{HTMLElement("input/time", "time")}}</td>
      <td><code>60</code> (ثانیه)</td>
      <td>
        افزایش‌های ۹۰۰ ثانیه‌ای (۱۵ دقیقه):<br />
        <code>&#x3C;input type="time" min="09:00" step="900"></code>
      </td>
    </tr>
    <tr>
      <td>
        {{HTMLElement("input/datetime-local", "datetime-local")}}
      </td>
      <td><code>1</code> (روز)</td>
      <td>
        همان روز هفته:<br />
        <code>&#x3C;input type="datetime-local" min="019-12-25T19:30"
          step="7"></code>
      </td>
    </tr>
    <tr>
      <td>{{HTMLElement("input/number", "number")}}</td>
      <td><code>1</code></td>
      <td>
        افزایش‌های ۰٫۱:<br />
        <code>&#x3C;input type="number" min="0" step="0.1" max="10"></code>
      </td>
    </tr>
    <tr>
      <td>{{HTMLElement("input/range", "range")}}</td>
      <td><code>1</code></td>
      <td>
        افزایش‌های ۲ تایی:<br />
        <code>&#x3C;input type="range" min="0" step="2" max="10"></code>
      </td>
    </tr>
  </thead>
</table>

این متد هنگام فراخوانی، مقدار کنترل فرم را به اندازه‌ی مقدار داده شده در ویژگی `step` ضرب‌در پارامتر، در محدوده‌ی قیود تعیین‌شده روی کنترل فرم تغییر می‌دهد. مقدار پیش‌فرض پارامتر در صورت عدم ارسال مقدار، `1` است. این متد باعث نمی‌شود که مقدار از مقدار تعیین‌شده‌ی [`max`](/en-US/docs/Web/HTML/Reference/Attributes/max) فراتر رود یا قیود تعیین‌شده توسط ویژگی [`step`](/en-US/docs/Web/HTML/Reference/Attributes/step) را نقض کند.

اگر مقدار قبل از فراخوانی متد `stepUp()` نامعتبر باشد – برای مثال، با قیود تعیین‌شده توسط ویژگی step مطابقت نداشته باشد – فراخوانی متد `stepUp()` مقداری را برمی‌گرداند که با قیود کنترل فرم مطابقت داشته باشد.

اگر کنترل فرم از نوع غیر زمانی، تاریخی یا عددی باشد و بنابراین از ویژگی `step` پشتیبانی نکند (لیست انواع ورودی پشتیبانی‌شده را در جدول بالا ببینید)، یا اگر مقدار step برابر `any` تنظیم شده باشد، یک استثنا از نوع `InvalidStateError` پرتاب می‌شود.

## نحو

```js-nolint
stepUp()
stepUp(stepIncrement)
```

### پارامترها

- `stepIncrement` {{optional_inline}}
  - : یک مقدار عددی. اگر پارامتری ارسال نشود، `stepIncrement` برابر `1` در نظر گرفته می‌شود.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مثال‌ها

روی دکمه در این مثال کلیک کنید تا نوع ورودی {{HTMLElement("input/number", "number")}} افزایش یابد:

### HTML

```html
<p>
  <label for="theNumber">
    عددی بین 0 تا 400 که بر 5 بخش‌پذیر است وارد کنید:
  </label>
  <input type="number" step="5" id="theNumber" min="0" max="400" />
</p>
<p>
  <label>
    تعداد مراحل گامی که می‌خواهید افزایش دهید را وارد کنید (یا خالی بگذارید):
  </label>
  <input type="number" step="1" id="incrementInput" min="0" max="25" />
</p>
<input type="button" value="افزایش" id="theButton" />
```

### JavaScript

```js
/* دکمه را برای فراخوانی تابع تنظیم کنید */
const button = document.getElementById("theButton");
button.addEventListener("click", () => {
  stepOnUp();
});

function stepOnUp() {
  let input = document.getElementById("theNumber");
  let val = document.getElementById("incrementInput").value;

  if (val) {
    /* افزایش با پارامتر */
    input.stepUp(val);
  } else {
    /* یا بدون پارامتر. با 0 امتحان کنید */
    input.stepUp();
  }
}
```

### CSS

```css
input:invalid {
  border: red solid 3px;
}
```

### نتیجه

{{EmbedLiveSample("Examples")}}

توجه کنید که اگر پارامتری به متد `stepUp` ارسال نکنید، مقدار پیش‌فرض آن `1` است. هر مقدار دیگر ضریبی از مقدار ویژگی `step` است که در اینجا `5` می‌باشد. اگر `4` را به عنوان `stepIncrement` ارسال کنید، ورودی به اندازه‌ی `4 * 5` یا `20` افزایش می‌یابد. اگر پارامتر `0` باشد، عدد افزایش نمی‌یابد. `stepUp` اجازه نمی‌دهد ورودی از محدوده خارج شود، در اینجا هنگام رسیدن به `400` متوقف می‌شود و هر عدد اعشاری که به عنوان پارامتر ارسال شود را به پایین گرد می‌کند.

سعی کنید ورودی افزایش گام را روی `1.2` تنظیم کنید. هنگام فراخوانی متد چه اتفاقی می‌افتد؟

سعی کنید مقدار را روی `4` تنظیم کنید که معتبر نیست. هنگام فراخوانی متد چه اتفاقی می‌افتد؟

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("input")}}
- {{domxref("HTMLInputElement")}}
- {{domxref("HTMLInputElement.stepDown")}}
- ویژگی‌های [`step`](/en-US/docs/Web/HTML/Reference/Attributes/step)، [`min`](/en-US/docs/Web/HTML/Reference/Attributes/min) و [`max`](/en-US/docs/Web/HTML/Reference/Attributes/max)
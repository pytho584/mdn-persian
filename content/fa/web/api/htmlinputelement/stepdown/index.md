---
title: "HTMLInputElement: stepDown() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/HTMLInputElement/stepDown"
---

---
title: "HTMLInputElement: stepDown() method"
short-title: stepDown()
slug: Web/API/HTMLInputElement/stepDown
page-type: web-api-instance-method
browser-compat: api.HTMLInputElement.stepDown
---

{{APIRef("HTML DOM")}}

متد **`HTMLInputElement.stepDown()`** مقدار عنصر {{HTMLElement("input")}} از نوع عددی را به اندازه‌ی مقدار ویژگی [`step`](/en-US/docs/Web/HTML/Reference/Attributes/step) کاهش می‌دهد، یا اگر عددی به‌عنوان پارامتر ارسال شود، آن را تا `n` برابرِ مقدار `step` کاهش می‌دهد.

این متد هنگام فراخوانی، مقدار [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value) را به اندازه‌ی ([`step`](/en-US/docs/Web/HTML/Reference/Elements/input#step) × n) کاهش می‌دهد؛ در این‌جا اگر n مشخص نشده باشد، پیش‌فرض آن `1` است و اگر [`step`](/en-US/docs/Web/HTML/Reference/Attributes/step) مشخص نشده باشد، پیش‌فرض آن مقدارِ پیش‌فرضِ `step` خواهد بود.

این متد برای همه‌ی انواع ورودیِ عددی، تاریخ و زمان که از ویژگی step پشتیبانی می‌کنند معتبر است، از جمله {{HTMLElement("input/date", "date")}}، {{HTMLElement("input/month", "month")}}، {{HTMLElement("input/week", "week")}}، {{HTMLElement("input/time", "time")}}، {{HTMLElement("input/datetime-local", "datetime-local")}}، {{HTMLElement("input/number", "number")}} و {{HTMLElement("input/range", "range")}}.

با در نظر گرفتن `<input id="myTime" type="time" max="17:00" step="900" value="17:00">`، فراخوانیِ `myTime.stepDown(3)` مقدار را به 16:15 تغییر می‌دهد؛ یعنی زمان به اندازه‌ی `3 × 900` یا ۴۵ دقیقه کاهش می‌یابد. همچنین `myTime.stepDown()` بدون پارامتر، چون `n` پیش‌فرض `1` دارد، نتیجه‌ی `16:45` را به همراه خواهد داشت.

```html
<!-- کاهش با بازه‌های ۹۰۰ ثانیه‌ای (۱۵ دقیقه) -->
<input type="time" max="17:00" step="900" />

<!-- کاهش با بازه‌های ۷ روزه (یک هفته) -->
<input type="date" max="2019-12-25" step="7" />

<!-- کاهش با بازه‌های ۱۲ ماهه (یک سال) -->
<input type="month" max="2019-12" step="12" />
```

با این حال، فراخوانیِ `stepDown` روی `<input type="time" max="17:00" step="900">` مقدار را آن‌طور که انتظار می‌رود روی `17:00` قرار نمی‌دهد — برخلاف `stepUp` وقتی ورودی `<input type="time" min="17:00" step="900">` باشد. در عوض، اولین فراخوانیِ `stepDown` مقدار اولیه را روی `23:45` قرار می‌دهد، حتی با وجود اینکه ویژگی `max` تنظیم شده است. دومین فراخوانی مقدار را روی `17:00` و سومین فراخوانی نیز مقدار را روی `16:45` قرار می‌دهد.

```js
let input1 = document.createElement("input");
input1.setAttribute("type", "time");
input1.setAttribute("min", "17:00");
input1.setAttribute("step", 900);
console.log(input1.value); // ""
input1.stepUp();
console.log(input1.value); // "17:00"
// اما
let input2 = document.createElement("input");
input2.setAttribute("type", "time");
input2.setAttribute("max", "17:00");
input2.setAttribute("step", 900);
console.log(input2.value); // ""
input2.stepDown();
console.log(input2.value); // "23:45"
input2.stepDown();
console.log(input2.value); // "17:00"
input2.stepDown();
console.log(input2.value); // "16:45"
```

این متد هنگام فراخوانی، مقدار کنترل فرم را به اندازه‌ی مقدارِ مشخص‌شده در ویژگی `step` ضرب‌در پارامتر، و در چارچوب محدودیت‌های تعیین‌شده در کنترل فرم تغییر می‌دهد. مقدار پیش‌فرض پارامتر، اگر ارسال نشود، ۱ است. این متد باعث نمی‌شود مقدار از [`min`](/en-US/docs/Web/HTML/Reference/Attributes/min) تعیین‌شده پایین‌تر برود یا محدودیت‌های اعمال‌شده توسط ویژگی [`step`](/en-US/docs/Web/HTML/Reference/Attributes/step) نقض شود. مقدار منفی برای `n` مقدار را افزایش می‌دهد، اما از مقدار [`max`](/en-US/docs/Web/HTML/Reference/Attributes/max) فراتر نمی‌رود.

اگر مقدار قبل از فراخوانی متد `stepDown()` نامعتبر باشد، مثلاً با محدودیت‌های ویژگی `step` مطابقت نداشته باشد، فراخوانی متد `stepDown()` مقداری برمی‌گرداند که با محدودیت‌های کنترل فرم مطابقت دارد.

اگر کنترل فرم از نوع غیر زمانی، تاریخ یا عددی باشد و بنابراین از ویژگی `step` پشتیبانی نکند (فهرست انواع ورودی‌های پشتیبانی‌شده را در بالا ببینید)، یا اگر مقدار `step` برابر با `any` تنظیم شده باشد، استثنای `InvalidStateError` پرتاب می‌شود.

## Syntax

```js-nolint
stepDown()
stepDown(stepDecrement)
```

### Parameters

- `stepDecrement` {{optional_inline}}
  - : یک مقدار عددی. اگر پارامتری ارسال نشود، _stepDecrement_ به‌صورت پیش‌فرض ۱ است.

    اگر مقدار اعشاری (float) باشد، مقدار به گونه‌ای کاهش می‌یابد که گویی [`Math.floor(stepDecrement)`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/floor) ارسال شده است. اگر مقدار منفی باشد، مقدار به‌جای کاهش، افزایش می‌یابد.

### Return value

هیچ ({{jsxref("undefined")}}).

## Exceptions

- `InvalidStateError` {{domxref("DOMException")}}
  - : در یکی از موارد زیر پرتاب می‌شود:
    - اگر متد برای مقدار فعلی [`type`](/en-US/docs/Web/HTML/Reference/Elements/input#type) قابل استفاده نباشد،
    - اگر عنصر هیچ مقدار [`step`](/en-US/docs/Web/HTML/Reference/Elements/input#step) نداشته باشد،
    - اگر [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value) نتواند به عدد تبدیل شود،
    - اگر مقدار حاصل بالاتر از [`max`](/en-US/docs/Web/HTML/Reference/Elements/input#max) یا پایین‌تر از [`min`](/en-US/docs/Web/HTML/Reference/Elements/input#min) باشد.

## Examples

در این مثال، روی دکمه کلیک کنید تا مقدار ورودی از نوع {{HTMLElement("input/number", "number")}} کاهش یابد:

### HTML

```html
<p>
  <label for="theNumber">
    عددی بین 0 تا 400 وارد کنید که بر 5 بخش‌پذیر باشد:
  </label>
  <input type="number" step="5" id="theNumber" min="0" max="400" />
</p>
<p>
  <label for="decrementButton">
    مشخص کنید مقدار step چند بار کاهش یابد یا آن را خالی بگذارید:
  </label>
  <input type="number" step="1" id="decrementInput" min="-2" max="15" />
</p>
<input type="button" value="Decrement" id="theButton" />
```

### JavaScript

```js
/* فراخوانی تابع با کلیک روی دکمه */
let button = document.getElementById("theButton");
button.addEventListener("click", () => {
  stepOnDown();
});

function stepOnDown() {
  let input = document.getElementById("theNumber");
  let val = document.getElementById("decrementInput").value;

  if (val) {
    // کاهش با پارامتر
    input.stepDown(val);
  } else {
    // یا بدون پارامتر. با مقادیری مانند 0، 5، 2- و غیره آزمایش کنید.
    input.stepDown();
  }
}
```

### CSS

```css
input:invalid {
  border: red solid 3px;
}
```

### Result

{{EmbedLiveSample("Examples")}}

توجه داشته باشید که اگر پارامتری به متد `stepDown()` ارسال نکنید، به‌صورت پیش‌فرض ۱ در نظر گرفته می‌شود. هر مقدار دیگر، ضریبی از مقدار ویژگی `step` است که در این‌جا ۵ است. اگر مقدار `4` را به‌عنوان `stepDecrement` ارسال کنیم، ورودی به اندازه‌ی `4 × 5` یعنی ۲۰ کاهش می‌یابد. اگر پارامتر `0` باشد، عدد کاهش نمی‌یابد. متد `stepDown()` اجازه نمی‌دهد مقدار ورودی از محدوده خارج شود؛ در این‌جا وقتی به ۰ برسد متوقف می‌شود و هر عدد اعشاری که به‌عنوان پارامتر ارسال شود به پایین گرد می‌شود.

سعی کنید مقدار ورودیِ decrement را روی `1.2` تنظیم کنید. هنگام فراخوانی متد چه اتفاقی می‌افتد؟

مقدار را روی `44` تنظیم کنید که نامعتبر است. هنگام فراخوانی متد چه اتفاقی می‌افتد؟

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{HTMLElement("input")}}
- {{domxref("HTMLInputElement")}}
- {{domxref("HTMLInputElement.stepUp", "HTMLInputElement.stepUp()")}}
- ویژگی‌های [`step`](/en-US/docs/Web/HTML/Reference/Attributes/step)، [`min`](/en-US/docs/Web/HTML/Reference/Attributes/min) و [`max`](/en-US/docs/Web/HTML/Reference/Attributes/max)
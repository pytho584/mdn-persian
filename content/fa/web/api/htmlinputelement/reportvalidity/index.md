---
title: "HTMLInputElement: reportValidity() method"
short-title: reportValidity()
slug: Web/API/HTMLInputElement/reportValidity
page-type: web-api-instance-method
browser-compat: api.HTMLInputElement.reportValidity
---

{{APIRef("HTML DOM")}}

متد **`reportValidity()`** از رابط {{domxref("HTMLInputElement")}} همان مراحل بررسی اعتبار را که متد {{domxref("HTMLInputElement.checkValidity", "checkValidity()")}} انجام می‌دهد، انجام می‌دهد. علاوه بر این، اگر رویداد {{domxref("HTMLElement/invalid_event", "invalid")}} لغو نشود، مرورگر مشکل را به کاربر نمایش می‌دهد.

## نحو

```js-nolint
reportValidity()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

در صورتی که مقدار عنصر هیچ مشکل اعتباری نداشته باشد، `true` و در غیر این صورت `false` برمی‌گرداند.

## مثال‌ها

### استفاده پایه

#### HTML

یک فرم شامل یک فیلد عددی اجباری (required) و دو دکمه قرار می‌دهیم: یکی برای بررسی فرم و دیگری برای ارسال آن.

```html
<form action="#" method="post">
  <p>
    <label for="age">Your (21 to 65) </label>
    <input type="number" name="age" required id="age" min="21" max="65" />
  </p>
  <p>
    <button type="submit">Submit</button>
    <button type="button" id="report">reportValidity()</button>
  </p>
  <p id="log"></p>
</form>
```

#### جاوااسکریپت

هنگامی که دکمه «reportValidity()» فعال می‌شود، از متد `reportValidity()` برای بررسی اینکه آیا مقدار ورودی با محدودیت‌های آن مطابقت دارد استفاده می‌کنیم. مقدار بازگشتی را ثبت می‌کنیم. اگر `false` باشد، پیام اعتبارسنجی را نیز نمایش می‌دهیم و رویداد `invalid` را دریافت می‌کنیم.

```js
const output = document.querySelector("#log");
const reportButton = document.querySelector("#report");
const ageInput = document.querySelector("#age");

ageInput.addEventListener("invalid", () => {
  console.log("Invalid event fired.");
});

reportButton.addEventListener("click", () => {
  const reportVal = ageInput.reportValidity();
  output.innerHTML = `"reportValidity()" returned: ${reportVal}`;
  if (!reportVal) {
    output.innerHTML += `<br />Validation message: "${ageInput.validationMessage}"`;
  }
});
```

#### نتایج

{{EmbedLiveSample("Basic usage", "100%", 120)}}

هنگامی که `false` باشد، اگر مقدار خالی باشد، کمتر از ۲۱ باشد، بیشتر از ۶۵ باشد، یا به هر شکل نامعتبر باشد، یک پیام خطا ظاهر می‌شود، رویداد `invalid` فعال می‌شود و ما آن رویداد را در کنسول ثبت می‌کنیم.

### پیام خطای سفارشی

این مثال نشان می‌دهد که چگونه یک پیام خطای سفارشی می‌تواند باعث شود متد `false` برگرداند در حالی که مقدار در غیر این صورت معتبر است.

#### HTML

یک دکمه «Fix me» به HTML مثال قبلی اضافه می‌کنیم.

```html hidden
<form action="#" method="post">
  <p>
    <label for="age">Your (21 to 65) </label>
    <input type="number" name="age" required id="age" min="21" max="65" />
  </p>
  <p>
    <button type="submit">Submit</button>
    <button type="button" id="report">reportValidity()</button>
    <button type="button" id="fix">Fix issues</button>
  </p>
  <p id="log"></p>
</form>
```

#### جاوااسکریپت

ما JavaScript مثال پایه بالا را گسترش می‌دهیم و یک تابع اضافه می‌کنیم که از متد {{domxref("HTMLInputElement.setCustomValidity()")}} برای ارائه پیام‌های خطای سفارشی استفاده می‌کند. تابع `validateAge()` فقط اگر ورودی معتبر باشد و متغیر `enableValidation` برابر `true` باشد، پیام خطا را به رشته خالی تنظیم می‌کند؛ `enableValidation` تا زمانی که دکمه «fix issues» فعال نشده باشد، `false` باقی می‌ماند.

```js
const output = document.querySelector("#log");
const reportButton = document.querySelector("#report");
const ageInput = document.querySelector("#age");
const fixButton = document.querySelector("#fix");
let enableValidation = false;

fixButton.addEventListener("click", (e) => {
  enableValidation = true;
  fixButton.innerHTML = "Error fixed";
  fixButton.disabled = true;
});

reportButton.addEventListener("click", () => {
  validateAge();
  const reportVal = ageInput.reportValidity();
  output.innerHTML = `"reportValidity()" returned: ${reportVal}`;
  if (!reportVal) {
    output.innerHTML += `<br />Validation message: "${ageInput.validationMessage}"`;
  }
});

function validateAge() {
  const validityState = ageInput.validity;
  if (validityState.valueMissing) {
    ageInput.setCustomValidity("Please set an age (required)");
  } else if (validityState.rangeUnderflow) {
    ageInput.setCustomValidity("Your value is too low");
  } else if (validityState.rangeOverflow) {
    ageInput.setCustomValidity("Your value is too high");
  } else if (enableValidation) {
    // sets to empty string if valid AND enableValidation has been set to true
    ageInput.setCustomValidity("");
  }
}
```

#### نتایج

{{EmbedLiveSample("Custom error message", "100%", 120)}}

اگر قبل از وارد کردن سن، دکمه «reportValidity()» را فعال کنید، متد `reportValidity()` مقدار `false` برمی‌گرداند، زیرا محدودیت اعتبارسنجی `required` برآورده نشده است. این متد رویداد `invalid` را روی ورودی فعال می‌کند و مشکل را به کاربر گزارش می‌دهد و پیام خطای سفارشی «Please set an age (required)» را نمایش می‌دهد. تا زمانی که یک پیام خطای سفارشی تنظیم شده باشد، فعال کردن دکمه «reportValidity()» همچنان یک خطا نمایش می‌دهد، حتی اگر سن معتبری انتخاب کنید. برای فعال کردن اعتبارسنجی، باید پیام خطای سفارشی را به رشته خالی تنظیم کنیم، که با کلیک روی دکمه «Fix issues» انجام می‌شود.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLInputElement.checkValidity()")}}
- {{HTMLElement("input")}}
- {{HTMLElement("form")}}
- [یادگیری: اعتبارسنجی فرم در سمت کلاینت](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [راهنما: اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation)
- شبه‌کلاس‌های CSS {{cssxref(":valid")}} و {{cssxref(":invalid")}}
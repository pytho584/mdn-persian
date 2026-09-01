---
title: "HTMLButtonElement: reportValidity() method"
short-title: reportValidity()
slug: Web/API/HTMLButtonElement/reportValidity
page-type: web-api-instance-method
browser-compat: api.HTMLButtonElement.reportValidity
---

{{APIRef("HTML DOM")}}

متد **`reportValidity()`** در رابط {{domxref("HTMLButtonElement")}} همان مراحل بررسی اعتبار را که در متد {{domxref("HTMLButtonElement.checkValidity", "checkValidity()")}} انجام می‌شود، اجرا می‌کند. علاوه بر این، اگر رویداد {{domxref("HTMLElement/invalid_event", "invalid")}} لغو (cancel) نشود، مرورگر مشکل را به کاربر نمایش می‌دهد.

## نحو (Syntax)

```js-nolint
reportValidity()
```

### پارامترها

هیچ.

### مقدار بازگشتی

اگر مقدار عنصر هیچ مشکل اعتباری نداشته باشد، `true` و در غیر این صورت `false` برمی‌گرداند.

### مثال‌ها

این مثال دور از ذهن نشان می‌دهد که چگونه می‌توان یک دکمه را نامعتبر کرد.

#### HTML

فرمی می‌سازیم که فقط چند دکمه دارد:

```html
<form action="#" id="form" method="post">
  <p>
    <input type="submit" value="Submit" />
    <button id="example" type="submit" value="fixed">THIS BUTTON</button>
  </p>
  <p>
    <button type="button" id="report">reportValidity()</button>
  </p>
</form>

<p id="log"></p>
```

#### CSS

مقداری CSS اضافه می‌کنیم، از جمله استایل‌های `:valid` و `:invalid` برای دکمه:

```css
input[type="submit"],
button {
  background-color: #3333aa;
  border: none;
  font-size: 1.3rem;
  padding: 5px 10px;
  color: white;
}
button:invalid {
  background-color: #aa3333;
}
button:valid {
  background-color: #33aa33;
}
```

#### JavaScript

تابعی برای تغییر مقدار، محتوا و پیام اعتبارسنجی دکمه مثال اضافه می‌کنیم:

```js
const reportButton = document.querySelector("#report");
const exampleButton = document.querySelector("#example");
const output = document.querySelector("#log");

reportButton.addEventListener("click", () => {
  const reportVal = exampleButton.reportValidity();
  output.innerHTML = `reportValidity returned: ${reportVal} <br/> custom error: ${exampleButton.validationMessage}`;
});

exampleButton.addEventListener("invalid", () => {
  console.log("Invalid event fired on exampleButton");
});

exampleButton.addEventListener("click", (e) => {
  e.preventDefault();
  if (exampleButton.value === "error") {
    breakOrFixButton("fixed");
  } else {
    breakOrFixButton("error");
  }
  output.innerHTML = `validation message: ${exampleButton.validationMessage} <br/> custom error: ${exampleButton.validationMessage}`;
});

function breakOrFixButton() {
  const state = toggleButton();
  if (state === "error") {
    exampleButton.setCustomValidity("This is a custom error message");
  } else {
    exampleButton.setCustomValidity("");
  }
}

function toggleButton() {
  if (exampleButton.value === "error") {
    exampleButton.value = "fixed";
    exampleButton.innerHTML = "No error";
  } else {
    exampleButton.value = "error";
    exampleButton.innerHTML = "Custom error";
  }
  return exampleButton.value;
}
```

#### نتیجه

{{EmbedLiveSample("Custom error message", "100%", 220)}}

دکمه به‌طور پیش‌فرض معتبر است. روی «THIS BUTTON» کلیک کنید تا مقدار، محتوا و یک پیام خطای سفارشی اضافه شود. با فعال‌کردن دکمه «reportValidity()» اعتبار دکمه بررسی می‌شود؛ اگر دکمه به دلیل این پیام، تأیید محدودیت‌ها (constraint validation) را رد کند، پیام خطای سفارشی به کاربر نمایش داده می‌شود و رویداد `invalid` صادر می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("HTMLButtonElement.checkValidity()")}}
- {{HTMLElement("button")}}
- {{HTMLElement("form")}}
- [یادگیری: اعتبارسنجی فرم در سمت کلاینت](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [راهنما: اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation)
- شبه‌کلاس‌های CSS {{cssxref(":valid")}} و {{cssxref(":invalid")}}
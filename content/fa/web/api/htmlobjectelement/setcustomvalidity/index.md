---
title: "HTMLObjectElement: setCustomValidity() method"
---

---
title: "HTMLObjectElement: setCustomValidity() method"
short-title: setCustomValidity()
slug: Web/API/HTMLObjectElement/setCustomValidity
page-type: web-api-instance-method
browser-compat: api.HTMLObjectElement.setCustomValidity
---

متد **`setCustomValidity()`** از رابط {{domxref("HTMLObjectElement")}} یک پیام اعتبارسنجی سفارشی برای عنصر تنظیم می‌کند.

## سینتکس

```js-nolint
setCustomValidity(errorMessage)
```

### پارامترها

- `errorMessage`
  - : پیامی که برای خطاهای اعتبارسنجی استفاده می‌شود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

هیچ.

## مثال‌ها

در این مثال، شناسه (ID) یک عنصر ورودی را پاس می‌کنیم و بسته به اینکه مقدار وجود نداشته باشد، بیش از حد کم باشد یا بیش از حد زیاد باشد، پیام‌های خطای متفاوتی تنظیم می‌کنیم. توجه داشته باشید که پیام بلافاصله نمایش داده نمی‌شود. تلاش برای ارسال فرم، پیام را نمایش می‌دهد، یا می‌توانید متد [`reportValidity()`](/en-US/docs/Web/API/HTMLInputElement/reportValidity) را روی عنصر صدا بزنید.

```js
function validate(inputID) {
  const input = document.getElementById(inputID);
  const validityState = input.validity;

  if (validityState.valueMissing) {
    input.setCustomValidity("You gotta fill this out, yo!");
  } else if (validityState.rangeUnderflow) {
    input.setCustomValidity("We need a higher number!");
  } else if (validityState.rangeOverflow) {
    input.setCustomValidity("Thats too high!");
  } else {
    input.setCustomValidity("");
  }

  input.reportValidity();
}
```

ضروری است که در نبود خطا، پیام به یک رشته خالی تنظیم شود. تا زمانی که پیام خطا خالی نباشد، فرم اعتبارسنجی را پاس نمی‌کند و ارسال نخواهد شد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref('validityState')}}
- {{domxref('validityState.valueMissing')}}
- {{domxref('validityState.typeMismatch')}}
- {{domxref('validityState.patternMismatch')}}
- {{domxref('validityState.tooLong')}}
- {{domxref('validityState.tooShort')}}
- {{domxref('validityState.rangeUnderflow')}}
- {{domxref('validityState.rangeOverflow')}}
- {{domxref('validityState.stepMismatch')}}
- {{domxref('validityState.valid')}}
- {{domxref('validityState.customError')}}
---
title: "Event: preventDefault() method"
---

---
title: "Event: preventDefault() method"
short-title: preventDefault()
slug: Web/API/Event/preventDefault
page-type: web-api-instance-method
browser-compat: api.Event.preventDefault
---

{{APIRef("DOM")}}{{AvailableInWorkers}}

متد **`preventDefault()`** در رابط {{domxref("Event")}} به {{Glossary("user agent")}} اعلام می‌کند که رویداد به‌طور صریح مدیریت شده است؛ بنابراین اقدام پیش‌فرض آن، مانند اسکرول صفحه، پیمایشِ لینک یا چسباندن متن، نباید انجام شود.

رویداد مانند همیشه به انتشار ادامه می‌دهد، مگر اینکه یکی از شنوندگان رویداد (event listener) آن، متد {{domxref("Event.stopPropagation", "stopPropagation()")}} یا {{domxref("Event.stopImmediatePropagation", "stopImmediatePropagation()")}} را فراخوانی کند؛ هر یک از این دو روش، انتشار رویداد را بلافاصله متوقف می‌کنند.

همان‌طور که در ادامه اشاره شد، فراخوانی **`preventDefault()`** برای یک رویداد غیرقابل‌لغو (non-cancelable)، مانند رویدادی که از طریق {{domxref("EventTarget.dispatchEvent()")}} و بدون تعیین `cancelable: true` ارسال شده باشد، هیچ اثری ندارد.

اگر یک شنوندهٔ غیرفعال (passive listener) `preventDefault()` را فراخوانی کند، هیچ اتفاقی رخ نمی‌دهد و ممکن است یک هشدار در کنسول نمایش داده شود.

> [!NOTE]
> به دنبال جایگزین‌های بهتری برای مسدود کردن اقدام‌های پیش‌فرض به‌جای استفاده از `preventDefault()` باشید. برای مثال، می‌توانید از ویژگی `disabled` یا `readonly` روی یک کنترل فرم برای جلوگیری از تعامل با آن استفاده کنید، از [اعتبارسنجی محدودیت‌های HTML](/en-US/docs/Web/HTML/Guides/Constraint_validation) برای رد کردن ورودی نامعتبر بهره ببرید، یا از ویژگی {{cssxref("overflow")}} برای جلوگیری از اسکرول استفاده کنید.

## Syntax

```js-nolint
preventDefault()
```

### Parameters

هیچ.

### Return value

هیچ ({{jsxref("undefined")}}).

## Examples

### جلوگیری از مدیریت پیش‌فرض کلیک

تغییر وضعیت یک چک‌باکس (checkbox) اقدام پیش‌فرضِ کلیک روی آن است. این مثال نشان می‌دهد که چگونه می‌توان از انجام این کار جلوگیری کرد:

#### JavaScript

```js
const checkbox = document.querySelector("#id-checkbox");

checkbox.addEventListener("click", checkboxClick);

function checkboxClick(event) {
  const warn = "preventDefault() won't let you check this!\n";
  document.getElementById("output-box").innerText += warn;
  event.preventDefault();
}
```

#### HTML

```html
<p>Please click on the checkbox control.</p>

<form>
  <label for="id-checkbox">Checkbox:</label>
  <input type="checkbox" id="id-checkbox" />
</form>

<div id="output-box"></div>
```

#### Result

{{EmbedLiveSample("Blocking_default_click_handling")}}

## Notes

فراخوانی `preventDefault()` در هر مرحله از جریان رویداد (event flow) باعث لغو رویداد می‌شود؛ به این معنی که هیچ اقدام پیش‌فرضی که معمولاً در نتیجهٔ آن رویداد توسط پیاده‌سازی انجام می‌شود، رخ نخواهد داد.

می‌توانید از {{domxref("Event.cancelable")}} برای بررسی اینکه آیا رویداد قابل‌لغو است استفاده کنید. فراخوانی `preventDefault()` برای یک رویداد غیرقابل‌لغو هیچ اثری ندارد.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}
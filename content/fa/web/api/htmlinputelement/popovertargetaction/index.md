---
title: "HTMLInputElement: popoverTargetAction property"
short-title: popoverTargetAction
slug: Web/API/HTMLInputElement/popoverTargetAction
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.popoverTargetAction
---

{{APIRef("Popover API")}}

ویژگی **`popoverTargetAction`** در رابط {{domxref("HTMLInputElement")}}، عملی را که باید روی یک عنصر پاپاور انجام شود (`"hide"`، `"show"` یا `"toggle"`) دریافت و تنظیم می‌کند. این عنصر پاپاور توسط یک عنصر {{htmlelement("input")}} از نوع `type="button"` کنترل می‌شود.

این ویژگی مقدار ویژگی HTML [`popovertargetaction`](/en-US/docs/Web/HTML/Reference/Elements/button#popovertargetaction) را منعکس می‌کند.

## مقدار

یک مقدار شمارشی است. مقادیر ممکن عبارت‌اند از:

- `"hide"`
  - دکمه، یک پاپاور نمایش‌داده‌شده را پنهان می‌کند. اگر سعی کنید یک پاپاور را که از قبل پنهان است پنهان کنید، هیچ عملی انجام نمی‌شود.
- `"show"`
  - دکمه، یک پاپاور پنهان را نمایش می‌دهد. اگر سعی کنید یک پاپاور را که از قبل نمایش داده شده است نمایش دهید، هیچ عملی انجام نمی‌شود.
- `"toggle"`
  - دکمه، یک پاپاور را بین حالت نمایش و پنهان جابه‌جا می‌کند. اگر پاپاور پنهان باشد، نمایش داده می‌شود؛ اگر پاپاور در حال نمایش باشد، پنهان می‌شود. اگر `popoverTargetAction` تنظیم نشده باشد، `"toggle"` عمل پیش‌فرضی است که توسط دکمه کنترل انجام می‌شود.

## مثال‌ها

### تغییر وضعیت پاپاور با یک پاپاور خودکار

این مثال استفادهٔ پایه از API پاپاور را با مقدار `"toggle"` برای ویژگی `popoverTargetAction` نشان می‌دهد.
ویژگی `popover` روی [`"auto"`](/en-US/docs/Web/API/Popover_API/Using#auto_state_and_light_dismiss) تنظیم شده است، بنابراین پاپاور را می‌توان با کلیک کردن در خارج از ناحیهٔ پاپاور بست («رد شدن سبک» یا light-dismiss).

ابتدا یک عنصر [`<input>`](/en-US/docs/Web/HTML/Reference/Elements/input/button) از نوع `type="button"` تعریف می‌کنیم که از آن برای نمایش و پنهان کردن پاپاور استفاده خواهیم کرد، و همچنین یک `<div>` که پاپاور خواهد بود.
در این مورد، ویژگی HTML [`popovertargetaction`](/en-US/docs/Web/HTML/Reference/Elements/button#popovertargetaction) را روی دکمه یا ویژگی [`popover`](/en-US/docs/Web/HTML/Reference/Global_attributes/popover) را روی `<div>` تنظیم نمی‌کنیم، زیرا این کار را به صورت برنامه‌نویسی انجام خواهیم داد.

```html
<input id="toggleBtn" type="button" value="Toggle popover" />
<div id="mypopover">This is popover content!</div>
```

کد جاوااسکریپت ابتدا ارجاعی به عناصر `<div>` و `<input>` به دست می‌آورد.
سپس تابعی تعریف می‌کند تا پشتیبانی از popover را بررسی کند.

```js
const popover = document.getElementById("mypopover");
const toggleBtn = document.getElementById("toggleBtn");

// Check for popover API support.
function supportsPopover() {
  return Object.hasOwn(HTMLElement.prototype, "popover");
}
```

اگر API پاپاور پشتیبانی شود، کد ویژگی `popover` عنصر `<div>` را روی `"auto"` تنظیم می‌کند و آن را به عنوان هدف پاپاور دکمه تغییر وضعیت قرار می‌دهد.
سپس `popoverTargetAction` دکمه را روی `"toggle"` تنظیم می‌کنیم.
اگر API پاپاور پشتیبانی نشود، محتوای متنی عنصر `<div>` را تغییر می‌دهیم تا این موضوع را بیان کند و دکمه تغییر وضعیت را مخفی می‌کنیم.

```js
if (supportsPopover()) {
  // Set the <div> element to be an auto popover
  popover.popover = "auto";
  // Set the button popover target to be the popover
  toggleBtn.popoverTargetElement = popover;

  // Set that the button toggles popover visibility
  toggleBtn.popoverTargetAction = "toggle";
} else {
  popover.textContent = "Popover API not supported.";
  toggleBtn.hidden = true;
}
```

> [!NOTE]
> یک عنصر پاپاور به طور پیش‌فرض مخفی است، اما اگر API پشتیبانی نشود، عنصر شما «به طور معمول» نمایش داده می‌شود.

می‌توانید مثال زیر را امتحان کنید.
با تغییر وضعیت دکمه، پاپاور را نمایش دهید و پنهان کنید.
پاپاور «خودکار» همچنین با کلیک کردن در خارج از محدودهٔ متن پاپاور بسته می‌شود.

{{EmbedLiveSample("Toggle popover action with an auto popover", "100%")}}

### نمایش/پنهان‌کردن پاپاور با پاپاور دستی

این مثال نحوه استفاده از مقادیر `"show"` و `"hide"` ویژگی `popoverTargetAction` را نشان می‌دهد.

کد تقریباً مشابه مثال قبلی است، با این تفاوت که دو عنصر `<button>` وجود دارد و پاپاور روی [`"manual"`](/en-US/docs/Web/API/Popover_API/Using#using_manual_popover_state) تنظیم شده است.
یک پاپاور «دستی» باید به صراحت بسته شود و با کلیک کردن در خارج از ناحیهٔ پاپاور «به‌طور سبک» رد نمی‌شود (light dismissed).

```html
<input id="showBtn" type="button" value="Show popover" />
<input id="hideBtn" type="button" value="Hide popover" />
<div id="mypopover">This is popover content!</div>
```

```js
function supportsPopover() {
  return Object.hasOwn(HTMLElement.prototype, "popover");
}

const popover = document.getElementById("mypopover");
const showBtn = document.getElementById("showBtn");
const hideBtn = document.getElementById("hideBtn");

const popoverSupported = supportsPopover();

if (supportsPopover()) {
  // Set the <div> element be a manual popover
  popover.popover = "manual";

  // Set the button targets to be the popover
  showBtn.popoverTargetElement = popover;
  hideBtn.popoverTargetElement = popover;

  // Set the target actions to be show/hide
  showBtn.popoverTargetAction = "show";
  hideBtn.popoverTargetAction = "hide";
} else {
  popover.textContent = "Popover API not supported.";
  showBtn.hidden = true;
  hideBtn.hidden = true;
}
```

پاپاور را می‌توان با کلیک کردن بر دکمهٔ «نمایش پاپاور» نمایش داد و با استفاده از دکمهٔ «پنهان کردن پاپاور» بست.

{{EmbedLiveSample("Show/hide popover action with a manual popover", "100%")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی سراسری HTML [`popover`](/en-US/docs/Web/HTML/Reference/Global_attributes/popover)
- [API پاپاور](/en-US/docs/Web/API/Popover_API)
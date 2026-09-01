---
title: "HTMLButtonElement: popoverTargetAction property"
short-title: popoverTargetAction
slug: Web/API/HTMLButtonElement/popoverTargetAction
page-type: web-api-instance-property
browser-compat: api.HTMLButtonElement.popoverTargetAction
---

{{APIRef("Popover API")}}

خاصیت **`popoverTargetAction`** از رابط {{domxref("HTMLButtonElement")}}، عملیاتی را که باید روی یک عنصر پاپ‌آور (popover) که توسط یک دکمه کنترل می‌شود انجام شود (`"hide"`، `"show"`، یا `"toggle"`) تنظیم و دریافت می‌کند.

این خاصیت مقدار ویژگی HTML [`popovertargetaction`](/en-US/docs/Web/HTML/Reference/Elements/button#popovertargetaction) را منعکس می‌کند.

## مقدار

یک مقدار شمارشی (enumerated). مقادیر ممکن عبارتند از:

- `"hide"`
  - : دکمه یک پاپ‌آور نمایش‌داده‌شده را مخفی می‌کند. اگر تلاش کنید یک پاپ‌آور که قبلاً مخفی است را مخفی کنید، هیچ عملی انجام نخواهد شد.
- `"show"`
  - : دکمه یک پاپ‌آور مخفی را نمایش می‌دهد. اگر تلاش کنید یک پاپ‌آور که قبلاً در حال نمایش است را نمایش دهید، هیچ عملی انجام نخواهد شد.
- `"toggle"`
  - : دکمه وضعیت نمایش یک پاپ‌آور را بین نمایش و مخفی تغییر می‌دهد. اگر پاپ‌آور مخفی باشد، نمایش داده می‌شود؛ اگر در حال نمایش باشد، مخفی می‌شود. اگر `popoverTargetAction` تنظیم نشده باشد، `"toggle"` عملی پیش‌فرض است که توسط دکمه کنترل انجام می‌شود.

## مثال‌ها

### عملکرد toggle پاپ‌آور با یک پاپ‌آور خودکار (auto)

این مثال استفاده پایه از API پاپ‌آور را با مقدار `"toggle"` برای خاصیت `popoverTargetAction` نشان می‌دهد. ویژگی `popover` روی [`"auto"`](/en-US/docs/Web/API/Popover_API/Using#auto_state_and_light_dismiss) تنظیم شده است، بنابراین پاپ‌آور می‌تواند با کلیک در خارج از ناحیه پاپ‌آور بسته شود ("light-dismissed").

ابتدا یک عنصر HTML `<button>` تعریف می‌کنیم که برای نمایش و مخفی کردن پاپ‌آور استفاده می‌شود، و یک `<div>` که پاپ‌آور خواهد بود. در این مورد، ویژگی HTML [`popovertargetaction`](/en-US/docs/Web/HTML/Reference/Elements/button#popovertargetaction) را روی `<button>` یا ویژگی [`popover`](/en-US/docs/Web/HTML/Reference/Global_attributes/popover) را روی `<div>` تنظیم نمی‌کنیم، زیرا این کار را به صورت برنامه‌نویسی انجام خواهیم داد.

```html
<button id="toggleBtn">Toggle popover</button>
<div id="mypopover">This is popover content!</div>
```

کد جاوااسکریپت ابتدا به عناصر `<div>` و `<button>` دسترسی پیدا می‌کند. سپس یک تابع برای بررسی پشتیبانی از پاپ‌آور تعریف می‌کند.

```js
const popover = document.getElementById("mypopover");
const toggleBtn = document.getElementById("toggleBtn");

// Check for popover API support.
function supportsPopover() {
  return Object.hasOwn(HTMLElement.prototype, "popover");
}
```

اگر API پاپ‌آور پشتیبانی شود، کد ویژگی `popover` عنصر `<div>` را روی `"auto"` تنظیم می‌کند و آن را به عنوان هدف پاپ‌آور دکمه toggle قرار می‌دهد. سپس `popoverTargetAction` دکمه `<button>` را روی `"toggle"` تنظیم می‌کنیم. اگر API پاپ‌آور پشتیبانی نشود، محتوای متنی عنصر `<div>` را برای بیان این موضوع تغییر داده و دکمه toggle را مخفی می‌کنیم.

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
> یک عنصر پاپ‌آور به طور پیش‌فرض مخفی است، اما اگر API پشتیبانی نشود، عنصر شما «به صورت معمول» نمایش داده می‌شود.

می‌توانید مثال زیر را امتحان کنید. با کلیک روی دکمه، پاپ‌آور را نمایش داده و مخفی کنید. پاپ‌آور `"auto"` همچنین می‌تواند با کلیک در خارج از محدوده متن پاپ‌آور «به صورت سبک» (light dismissed) بسته شود.

{{EmbedLiveSample("Toggle popover action with an auto popover", "100%")}}

### عملکرد نمایش/مخفی کردن پاپ‌آور با یک پاپ‌آور دستی (manual)

این مثال نحوه استفاده از مقادیر `"show"` و `"hide"` ویژگی `popoverTargetAction` را نشان می‌دهد.

کد تقریباً مشابه مثال قبلی است، با این تفاوت که دو عنصر `<button>` وجود دارد و پاپ‌آور روی [`"manual"`](/en-US/docs/Web/API/Popover_API/Using#using_manual_popover_state) تنظیم شده است. یک پاپ‌آور `manual` باید به صراحت بسته شود و با کلیک در خارج از ناحیه پاپ‌آور «به صورت سبک» بسته نمی‌شود.

```html
<button id="showBtn">Show popover</button>
<button id="hideBtn">Hide popover</button>
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

پاپ‌آور با انتخاب دکمه «Show popover» نمایش داده می‌شود و با استفاده از دکمه «Hide popover» بسته می‌شود.

{{EmbedLiveSample("Show/hide popover action with a manual popover", "100%")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [API پاپ‌آور](/en-US/docs/Web/API/Popover_API)
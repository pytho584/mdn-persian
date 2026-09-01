---
title: "HTMLInputElement: popoverTargetAction property"
---

---
title: "HTMLInputElement: popoverTargetAction property"
short-title: popoverTargetAction
slug: Web/API/HTMLInputElement/popoverTargetAction
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.popoverTargetAction
---

{{APIRef("Popover API")}}

ویژگی **`popoverTargetAction`** در رابط {{domxref("HTMLInputElement")}}، عملیاتی که باید روی یک عنصر پاپاور انجام شود (`"hide"`، `"show"` یا `"toggle"`) را دریافت و تنظیم می‌کند؛ پاپاوری که توسط یک عنصر {{htmlelement("input")}} با `type="button"` کنترل می‌شود.

این ویژگی، مقدار صفت HTML [`popovertargetaction`](/en-US/docs/Web/HTML/Reference/Elements/button#popovertargetaction) را منعکس می‌کند.

## مقدار

یک مقدار شمارشی. مقادیر ممکن عبارت‌اند از:

- `"hide"`
  - دکمه یک پاپاورِ نمایش‌داده‌شده را پنهان می‌کند. اگر تلاش کنید پاپاوری را که از قبل پنهان است پنهان کنید، هیچ اقدامی انجام نمی‌شود.
- `"show"`
  - دکمه یک پاپاورِ پنهان را نمایش می‌دهد. اگر تلاش کنید پاپاوری را که از قبل در حال نمایش است نمایش دهید، هیچ اقدامی انجام نمی‌شود.
- `"toggle"`
  - دکمه وضعیت نمایش یک پاپاور را بین نمایش و پنهان‌بودن تغییر می‌دهد. اگر پاپاور پنهان باشد، نمایش داده می‌شود؛ اگر در حال نمایش باشد، پنهان می‌شود. اگر `popoverTargetAction` تنظیم نشده باشد، `"toggle"` اقدام پیش‌فرضی است که توسط دکمه کنترل‌کننده انجام می‌شود.

## مثال‌ها

### تغییر وضعیت پاپاور با یک پاپاور auto

این مثال کاربرد پایه API پاپاور را با مقدار «toggle» برای ویژگی `popoverTargetAction` نشان می‌دهد. صفت `popover` روی [`"auto"`](/en-US/docs/Web/API/Popover_API/Using#auto_state_and_light_dismiss) تنظیم شده است، بنابراین پاپاور را می‌توان با کلیک کردن در بیرون از ناحیه پاپاور بست («light dismiss»).

ابتدا یک [`<input>`](/en-US/docs/Web/HTML/Reference/Elements/input/button) با `type="button"` تعریف می‌کنیم که از آن برای نمایش و پنهان کردن پاپاور استفاده خواهیم کرد، و یک `<div>` که پاپاور خواهد بود. در این حالت، صفت HTML [`popovertargetaction`](/en-US/docs/Web/HTML/Reference/Elements/button#popovertargetaction) را روی دکمه و صفت [`popover`](/en-US/docs/Web/HTML/Reference/Global_attributes/popover) را روی `<div>` تنظیم نمی‌کنیم، چون این کار را به‌صورت برنامه‌نویسی انجام خواهیم داد.

```html
<input id="toggleBtn" type="button" value="Toggle popover" />
<div id="mypopover">This is popover content!</div>
```

کد جاوااسکریپت ابتدا ارجاعی به عناصر `<div>` و `<input>` می‌گیرد. سپس تابعی برای بررسی پشتیبانی از پاپاور تعریف می‌کند.

```js
const popover = document.getElementById("mypopover");
const toggleBtn = document.getElementById("toggleBtn");

// Check for popover API support.
function supportsPopover() {
  return Object.hasOwn(HTMLElement.prototype, "popover");
}
```

اگر API پاپاور پشتیبانی شود، کد صفت `popover` عنصر `<div>` را روی `"auto"` تنظیم می‌کند و آن را به هدف پاپاور دکمه تغییر وضعیت تبدیل می‌کند. سپس `popoverTargetAction` دکمه را روی `"toggle"` تنظیم می‌کنیم. اگر API پاپاور پشتیبانی نشود، محتوای متنی عنصر `<div>` را برای بیان این موضوع تغییر می‌دهیم و دکمه تغییر وضعیت را پنهان می‌کنیم.

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
> یک عنصر پاپاور به‌صورت پیش‌فرض پنهان است، اما اگر API پشتیبانی نشود، عنصر شما به شکل معمول نمایش داده می‌شود.

می‌توانید مثال زیر را امتحان کنید. با تغییر وضعیت دکمه، پاپاور را نمایش دهید و پنهان کنید. پاپاور «auto» را می‌توان با کلیک کردن در بیرون از محدوده متن پاپاور نیز بست.

{{EmbedLiveSample("Toggle popover action with an auto popover", "100%")}}

### اقدام نمایش/پنهان‌کردن پاپاور با یک پاپاور manual

این مثال نحوه استفاده از مقادیر `"show"` و `"hide"` ویژگی `popoverTargetAction` را نشان می‌دهد.

کد تقریباً مشابه مثال قبلی است، با این تفاوت که دو عنصر `<button>` وجود دارد و پاپاور روی [`"manual"`](/en-US/docs/Web/API/Popover_API/Using#using_manual_popover_state) تنظیم شده است. یک پاپاور `manual` باید به‌صورت صریح بسته شود و با کلیک کردن در بیرون از ناحیه پاپاور بسته نمی‌شود («light dismiss» نمی‌شود).

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

پاپاور را می‌توان با کلیک روی دکمه «Show popover» نمایش داد و با استفاده از دکمه «Hide popover» بست.

{{EmbedLiveSample("Show/hide popover action with a manual popover", "100%")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- صفت سراسری HTML [`popover`](/en-US/docs/Web/HTML/Reference/Global_attributes/popover)
- [Popover API](/en-US/docs/Web/API/Popover_API)
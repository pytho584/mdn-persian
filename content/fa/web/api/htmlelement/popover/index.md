---
title: "HTMLElement: popover property"
short-title: popover
slug: Web/API/HTMLElement/popover
page-type: web-api-instance-property
browser-compat: api.HTMLElement.popover
---

{{APIRef("Popover API")}}

خاصیت **`popover`** در رابط {{domxref("HTMLElement")}}، وضعیت پاپ‌آور یک عنصر را از طریق JavaScript (با مقادیر `"auto"`، `"hint"` یا `"manual"`) دریافت و تنظیم می‌کند و می‌توان از آن برای تشخیص ویژگی (feature detection) استفاده کرد.

این خاصیت منعکس‌کنندهٔ مقدار ویژگی سراسری HTML [`popover`](/en-US/docs/Web/HTML/Reference/Global_attributes/popover) است.

## Value

یک مقدار شمارشی (enumerated)؛ مقادیر ممکن عبارتند از:

- `"auto"`
  - پاپ‌آورهای `auto` را می‌توان با «بستن سبک» (light dismiss) پنهان کرد — یعنی با کلیک کردن در خارج از آن یا فشردن کلید <kbd>Esc</kbd> می‌توان پاپ‌آور را مخفی کرد.

    معمولاً فقط یک پاپ‌آور `auto` در یک زمان می‌تواند نمایش داده شود — نمایش یک پاپ‌آور دوم در حالی که یک پاپ‌آور قبلاً نمایش داده شده است، باعث پنهان شدن پاپ‌آور اول می‌شود. استثنای این قاعده زمانی است که پاپ‌آورهای `auto` تو در تو داشته باشید. برای جزئیات بیشتر به [پاپ‌آورهای تو در تو](/en-US/docs/Web/API/Popover_API/Using#nested_popovers) مراجعه کنید.

- `"hint"`
  - پاپ‌آورهای `hint` هنگام نمایش، پاپ‌آورهای `auto` را نمی‌بندند، اما سایر پاپ‌آورهای `hint` را می‌بندند. این پاپ‌آورها را می‌توان با بستن سبک پنهان کرد و به درخواست‌های بستن پاسخ می‌دهند. معمولاً در پاسخ به رویدادهای JavaScript غیر کلیکی مانند [`mouseover`](/en-US/docs/Web/API/Element/mouseover_event)/[`mouseout`](/en-US/docs/Web/API/Element/mouseout_event) و [`focus`](/en-US/docs/Web/API/Element/focus_event)/[`blur`](/en-US/docs/Web/API/Element/blur_event) نمایش داده یا پنهان می‌شوند. کلیک کردن روی یک دکمه برای باز کردن یک پاپ‌آور `hint` باعث می‌شود که یک پاپ‌آور `auto` باز شده با بستن سبک پنهان شود.

- `"manual"`
  - پاپ‌آورهای `manual` را نمی‌توان با «بستن سبک» پنهان کرد و به‌طور خودکار بسته نمی‌شوند. پاپ‌آورها باید به‌صراحت با استفاده از دکمه‌های اعلانی نمایش/پنهان/تغییر وضعیت (declarative show/hide/toggle buttons) یا JavaScript نمایش داده و بسته شوند. چندین پاپ‌آور `manual` مستقل می‌توانند هم‌زمان نمایش داده شوند.

## Examples

### تشخیص ویژگی (Feature detection)

می‌توانید از ویژگی `popover` برای تشخیص ویژگی (feature detection) [Popover API](/en-US/docs/Web/API/Popover_API) استفاده کنید:

```js
function supportsPopover() {
  return Object.hasOwn(HTMLElement.prototype, "popover");
}
```

### راه‌اندازی برنامه‌نویسی یک پاپ‌آور

```js
const popover = document.getElementById("mypopover");
const toggleBtn = document.getElementById("toggleBtn");

const popoverSupported = supportsPopover();

if (popoverSupported) {
  popover.popover = "auto";
  toggleBtn.popoverTargetElement = popover;
  toggleBtn.popoverTargetAction = "toggle";
} else {
  console.log("Popover API not supported.");
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [`popover`](/en-US/docs/Web/HTML/Reference/Global_attributes/popover) HTML global attribute
- [Popover API](/en-US/docs/Web/API/Popover_API)
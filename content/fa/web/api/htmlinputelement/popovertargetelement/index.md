---
title: "HTMLInputElement: popoverTargetElement property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/HTMLInputElement/popoverTargetElement"
---

---
title: "HTMLInputElement: popoverTargetElement property"
short-title: popoverTargetElement
slug: Web/API/HTMLInputElement/popoverTargetElement
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.popoverTargetElement
---

{{APIRef("Popover API")}}

ویژگی **`popoverTargetElement`** در رابط {{domxref("HTMLInputElement")}}، عنصر پاپ‌اور را که قرار است از طریق یک عنصر {{htmlelement("input")}} با `type="button"` کنترل شود، دریافت و تنظیم می‌کند.

این ویژگی معادل جاوااسکریپتی ویژگی HTML [`popovertarget`](/en-US/docs/Web/HTML/Reference/Elements/button#popovertarget) است.

برقراری ارتباط بین یک پاپ‌اور و دکمهٔ فراخوان آن با استفاده از ویژگی `popoverTargetElement` دو اثر مفید دیگر نیز دارد:

- مرورگر به‌طور ضمنی یک رابطهٔ [`aria-details`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-details) و [`aria-expanded`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-expanded) بین پاپ‌اور و فراخوان ایجاد می‌کند و هنگام نمایش، پاپ‌اور را در موقعیتی منطقی در ترتیب پیمایش با کلید صفحه‌کلید قرار می‌دهد. این امر پاپ‌اور را برای کاربران صفحه‌کلید و فناوری‌های کمکی (AT) در دسترس‌تر می‌سازد (همچنین به [ویژگی‌های دسترس‌پذیری پاپ‌اور](/en-US/docs/Web/API/Popover_API/Using#popover_accessibility_features) مراجعه کنید).
- مرورگر به‌طور ضمنی یک مرجع لنگر (anchor reference) بین این دو ایجاد می‌کند که جای‌دهی پاپ‌اورها را در کنار کنترل‌هایشان با استفاده از [موقعیت‌یابی لنگر CSS](/en-US/docs/Web/CSS/Guides/Anchor_positioning) بسیار آسان می‌سازد. برای جزئیات بیشتر، به [موقعیت‌یابی لنگر پاپ‌اور](/en-US/docs/Web/API/Popover_API/Using#popover_anchor_positioning) مراجعه کنید.

## مقدار

یک ارجاع به عنصر پاپ‌اور در DOM.

## نمونه‌ها

```js
function supportsPopover() {
  return Object.hasOwn(HTMLElement.prototype, "popover");
}

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

### عملکرد جابه‌جایی پاپ‌اور با یک پاپ‌اور خودکار

این مثال کاربرد اصلی API پاپ‌اور را نشان می‌دهد: تنظیم یک عنصر `<div>` به‌عنوان پاپ‌اور و سپس تنظیم آن به‌عنوان `popoverTargetElement` برای یک [`<input>`](/en-US/docs/Web/HTML/Reference/Elements/input/button) با `type="button"`.
ویژگی `popover` روی [`"auto"`](/en-US/docs/Web/API/Popover_API/Using#auto_state_and_light_dismiss) تنظیم شده است، بنابراین پاپ‌اور را می‌توان با کلیک کردن در خارج از ناحیهٔ پاپ‌اور بست («رد شدن سبک» یا light-dismiss).

ابتدا یک `<input>` تعریف می‌کنیم که برای نمایش و پنهان کردن پاپ‌اور از آن استفاده می‌کنیم و یک `<div>` که پاپ‌اور خواهد بود.
در این حالت، ویژگی HTML [`popovertargetaction`](/en-US/docs/Web/HTML/Reference/Elements/button#popovertargetaction) را روی `<input>` یا ویژگی [`popover`](/en-US/docs/Web/HTML/Reference/Global_attributes/popover) را روی `<div>` تنظیم نمی‌کنیم، زیرا این کار را به‌صورت برنامه‌نویسی انجام خواهیم داد.

```html
<input id="toggleBtn" type="button" value="Toggle popover" />
<div id="mypopover">This is popover content!</div>
```

کد جاوااسکریپت ابتدا به عناصر `<div>` و `<input>` دسترسی پیدا می‌کند.
سپس تابعی برای بررسی پشتیبانی از پاپ‌اور تعریف می‌کند.

```js
const popover = document.getElementById("mypopover");
const toggleBtn = document.getElementById("toggleBtn");

// Check for popover API support.
function supportsPopover() {
  return Object.hasOwn(HTMLElement.prototype, "popover");
}
```

اگر API پاپ‌اور پشتیبانی شود، کد ویژگی `popover` عنصر `<div>` را روی `"auto"` تنظیم می‌کند و آن را هدف پاپ‌اور دکمهٔ جابه‌جایی قرار می‌دهد.
سپس `popoverTargetAction` دکمه را روی `"toggle"` تنظیم می‌کنیم.
اگر API پاپ‌اور پشتیبانی نشود، متن محتوای عنصر `<div>` را تغییر می‌دهیم تا این موضوع را بیان کند و عنصر ورودی را پنهان می‌کنیم.

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
> یک عنصر پاپ‌اور به‌طور پیش‌فرض پنهان است، اما اگر API پشتیبانی نشود، عنصر شما «به‌صورت عادی» نمایش داده می‌شود.

می‌توانید نمونهٔ زیر را امتحان کنید.
پاپ‌اور را با جابه‌جا کردن دکمه نمایش دهید و پنهان کنید.
پاپ‌اور «خودکار» را نیز می‌توان با کلیک کردن در خارج از محدودهٔ متن پاپ‌اور به‌طور سبک رد کرد.

{{EmbedLiveSample("Toggle popover action with an auto popover", "100%")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی سراسری HTML [`popover`](/en-US/docs/Web/HTML/Reference/Global_attributes/popover)
- [API پاپ‌اور](/en-US/docs/Web/API/Popover_API)

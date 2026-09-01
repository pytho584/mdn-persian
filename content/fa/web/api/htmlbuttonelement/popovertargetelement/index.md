---
title: "HTMLButtonElement: popoverTargetElement property"
short-title: popoverTargetElement
slug: Web/API/HTMLButtonElement/popoverTargetElement
page-type: web-api-instance-property
browser-compat: api.HTMLButtonElement.popoverTargetElement
---

{{APIRef("Popover API")}}

ویژگی **`popoverTargetElement`** در رابط {{domxref("HTMLButtonElement")}}، عنصر popover ای را که قرار است توسط یک دکمه کنترل شود، دریافت و تنظیم می‌کند.

این ویژگی معادل جاوااسکریپتی ویژگی HTML [`popovertarget`](/en-US/docs/Web/HTML/Reference/Elements/button#popovertarget) است.

برقراری ارتباط بین یک popover و دکمه‌ی فراخوان آن با استفاده از ویژگی `popoverTargetElement` دو اثر مفید دیگر نیز دارد:

- مرورگر یک رابطه‌ی ضمنی [`aria-details`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-details) و [`aria-expanded`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-expanded) بین popover و فراخوان ایجاد می‌کند و هنگام نمایش، popover را در جایگاه منطقی در ترتیب پیمایش با صفحه‌کلید قرار می‌دهد. این کار باعث می‌شود popover برای کاربران صفحه‌کلید و فناوری کمکی (AT) در دسترس‌تر باشد (همچنین ببینید: [ویژگی‌های دسترس‌پذیری Popover](/en-US/docs/Web/API/Popover_API/Using#popover_accessibility_features)).
- مرورگر یک مرجع لنگر ضمنی بین این دو ایجاد می‌کند و بدین ترتیب، قرار دادن popover در کنار کنترل‌های مربوطه با استفاده از [قرارگیری لنگر CSS](/en-US/docs/Web/CSS/Guides/Anchor_positioning) بسیار آسان می‌شود. برای جزئیات بیشتر، به [قرارگیری لنگر Popover](/en-US/docs/Web/API/Popover_API/Using#popover_anchor_positioning) مراجعه کنید.

## مقدار

یک ارجاع به یک عنصر popover در DOM.

## مثال‌ها

### عملکرد تغییر وضعیت popover با popover خودکار

این مثال کاربرد اصلی API Popover را نشان می‌دهد: یک عنصر `<div>` به عنوان popover تنظیم می‌شود و سپس به عنوان `popoverTargetElement` یک دکمه `<button>` قرار می‌گیرد. ویژگی `popover` روی [`"manual"`](/en-US/docs/Web/API/Popover_API/Using#using_manual_popover_state) تنظیم شده است، بنابراین popover باید با یک دکمه بسته شود و با انتخاب خارج از ناحیه popover به‌صورت «نور» بسته نمی‌شود.

ابتدا یک عنصر `<button>` تعریف می‌کنیم که برای نمایش و مخفی‌کردن popover استفاده می‌شود و یک `<div>` که همان popover خواهد بود. در این حالت، ویژگی HTML [`popovertargetaction`](/en-US/docs/Web/HTML/Reference/Elements/button#popovertargetaction) را روی `<button>` یا ویژگی [`popover`](/en-US/docs/Web/HTML/Reference/Global_attributes/popover) را روی `<div>` تنظیم نمی‌کنیم، زیرا این کار را به‌صورت برنامه‌نویسی انجام خواهیم داد.

```html
<button id="toggleBtn">Toggle popover</button>
<div id="mypopover">This is popover content!</div>
```

کد جاوااسکریپت ابتدا به عناصر `<div>` و `<button>` دسترسی پیدا می‌کند. سپس تابعی تعریف می‌کند که پشتیبانی از popover را بررسی کند.

```js
const popover = document.getElementById("mypopover");
const toggleBtn = document.getElementById("toggleBtn");

// Check for popover API support.
function supportsPopover() {
  return Object.hasOwn(HTMLElement.prototype, "popover");
}
```

اگر API popover پشتیبانی شود، کد ویژگی `popover` عنصر `<div>` را روی `"auto"` تنظیم می‌کند و آن را هدف popover دکمه تغییر وضعیت قرار می‌دهد. سپس `popoverTargetAction` دکمه `<button>` را روی `"toggle"` قرار می‌دهیم. اگر API popover پشتیبانی نشود، متن داخل عنصر `<div>` را تغییر می‌دهیم تا این موضوع را اعلام کند و دکمه تغییر وضعیت را مخفی می‌کنیم.

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
> یک عنصر popover به‌طور پیش‌فرض مخفی است، اما اگر API پشتیبانی نشود، عنصر شما «به‌شکل معمول» نمایش داده می‌شود.

می‌توانید مثال زیر را امتحان کنید. با تغییر وضعیت دکمه، popover را نمایش داده و مخفی کنید. popover «خودکار» (auto) را می‌توان با انتخاب خارج از محدوده متن popover نیز بست.

{{EmbedLiveSample("Toggle popover action with an auto popover", "100%")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [API Popover](/en-US/docs/Web/API/Popover_API)
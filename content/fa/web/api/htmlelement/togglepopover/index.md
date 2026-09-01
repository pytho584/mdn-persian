---
title: "HTMLElement: togglePopover() method"
short-title: togglePopover()
slug: Web/API/HTMLElement/togglePopover
page-type: web-api-instance-method
browser-compat: api.HTMLElement.togglePopover
---

{{APIRef("Popover API")}}

متد **`togglePopover()`** از رابط {{domxref("HTMLElement")}} یک عنصر پاپ‌آور (popover) (یعنی عنصری که دارای ویژگی معتبر [`popover`](/en-US/docs/Web/HTML/Reference/Global_attributes/popover) است) را بین حالت‌های پنهان و نمایش داده شده جابه‌جا می‌کند.

هنگامی که `togglePopover()` روی یک عنصر با ویژگی [`popover`](/en-US/docs/Web/HTML/Reference/Global_attributes/popover) فراخوانی می‌شود:

1. رویداد {{domxref("HTMLElement/beforetoggle_event", "beforetoggle")}} فعال می‌شود.
2. پاپ‌آور بین حالت پنهان و نمایش داده شده جابه‌جا می‌شود:
   1. اگر ابتدا در حالت نمایش بود، به حالت پنهان می‌رود.
   2. اگر ابتدا پنهان بود، به حالت نمایش می‌رود.
3. رویداد {{domxref("HTMLElement/toggle_event", "toggle")}} فعال می‌شود.

## نحو (Syntax)

```js-nolint
togglePopover()
togglePopover(force)
togglePopover(options)
```

### پارامترها

یک مقدار بولی (`force`) یا یک شیء options:

- `force` {{optional_inline}}
  - : یک مقدار بولی که باعث می‌شود `togglePopover()` مانند {{domxref("HTMLElement.showPopover", "showPopover()")}} یا {{domxref("HTMLElement.hidePopover", "hidePopover()")}} عمل کند.
    - اگر `true` تنظیم شود، پاپ‌آور در صورتی که ابتدا پنهان بوده، نمایش داده می‌شود. اگر ابتدا نمایش داده شده باشد، هیچ اتفاقی نمی‌افتد.
    - اگر `false` تنظیم شود، پاپ‌آور در صورتی که ابتدا نمایش داده شده بود، پنهان می‌شود. اگر ابتدا پنهان بوده، هیچ اتفاقی نمی‌افتد.
- `options` {{optional_inline}}
  - : یک شیء که می‌تواند شامل ویژگی‌های زیر باشد:
    - `force` {{optional_inline}}
      - : یک مقدار بولی؛ به توضیحات `force` در بالا مراجعه کنید.
    - `source` {{optional_inline}}
      - : یک ارجاع {{domxref("HTMLElement")}}؛ به صورت برنامه‌نویسی فراخواننده (invoker) پاپ‌آور مرتبط با عمل جابه‌جایی را تعریف می‌کند، یعنی عنصر کنترل‌کننده آن. برقراری رابطه بین یک پاپ‌آور و فراخواننده آن با استفاده از گزینه `source` دو اثر مفید دارد:
        - مرورگر هنگام نمایش، پاپ‌آور را در موقعیت منطقی در ترتیب ناوبری با کلید Tab قرار می‌دهد. این کار پاپ‌آور را برای کاربران صفحه‌کلید در دسترس‌تر می‌کند (همچنین به [ویژگی‌های دسترسی پاپ‌آور](/en-US/docs/Web/API/Popover_API/Using#popover_accessibility_features) مراجعه کنید).
        - مرورگر یک ارجاع لنگر (anchor reference) ضمنی بین این دو ایجاد می‌کند که موقعیت‌دهی پاپ‌آورها نسبت به کنترل‌هایشان را با استفاده از [موقعیت‌دهی لنگر CSS](/en-US/docs/Web/CSS/Guides/Anchor_positioning) بسیار آسان می‌کند. برای جزئیات بیشتر به [موقعیت‌دهی لنگر پاپ‌آور](/en-US/docs/Web/API/Popover_API/Using#popover_anchor_positioning) مراجعه کنید.

### استثناها (Exceptions)

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر این متد در حالی فراخوانی شود که یک پاپ‌آور دیگر در حال نمایش یا پنهان شدن است (مثلاً درون یک شنونده رویداد `beforetoggle`)، پرتاب می‌شود.

### مقدار بازگشتی (Return value)

اگر پس از فراخوانی، پاپ‌آپ باز باشد `true` و در غیر این صورت `false` بازمی‌گرداند.

در نسخه‌های قدیمی‌تر مرورگرها ممکن است هیچ‌کدام ({{jsxref("undefined")}}) برگردانده شود (به [سازگاری مرورگر](#browser_compatibility) مراجعه کنید).

## مثال‌ها

برای دسترسی به مجموعه کامل مثال‌های پاپ‌آور MDN به [صفحه اصلی مثال‌های Popover API](https://mdn.github.io/dom-examples/popover-api/) مراجعه کنید.

### پاپ‌آپ خودکار ساده

این یک نسخه کمی تغییر یافته از [مثال پاپ‌آور راهنمای کاربری با جابه‌جایی](https://mdn.github.io/dom-examples/popover-api/toggle-help-ui/) است.
این مثال با فشار دادن یک کلید خاص روی صفحه‌کلید (زمانی که پنجره مثال فوکوس دارد) یک پاپ‌آور را روشن و خاموش می‌کند.

HTML این مثال در زیر نشان داده شده است.
این عنصر اول دستورالعمل‌هایی را برای نحوه فراخوانی پاپ‌آپ تعریف می‌کند، زیرا پاپ‌آپ‌ها به طور پیش‌فرض پنهان هستند.

```html
<p id="instructions">
  برای جابه‌جایی صفحه راهنما، کلید "h" را فشار دهید (ابتدا پنجره مثال را انتخاب کنید).
</p>
```

سپس یک عنصر `<div>` تعریف می‌کنیم که همان پاپ‌آپ است.
محتوای واقعی مهم نیست، اما توجه داشته باشید که برای تبدیل `<div>` به یک پاپ‌آور به ویژگی [`popover`](/en-US/docs/Web/HTML/Reference/Global_attributes/popover) نیاز داریم تا به طور پیش‌فرض پنهان باشد (یا می‌توانیم این عنصر را در جاوااسکریپت تنظیم کنیم).

```html
<div id="mypopover" popover>
  <h2>راهنما!</h2>

  <p>می‌توانید از دستورات زیر برای کنترل برنامه استفاده کنید</p>

  <ul>
    <li>برای سفارش پنیر، کلید <ins>C</ins> را فشار دهید</li>
    <li>برای سفارش توفو، کلید <ins>T</ins> را فشار دهید</li>
    <li>برای سفارش بیکن، کلید <ins>B</ins> را فشار دهید</li>
  </ul>
</div>
```

جاوااسکریپت این مثال در زیر نشان داده شده است.
ابتدا بررسی می‌کنیم که آیا پاپ‌آورها پشتیبانی می‌شوند یا خیر، و اگر پشتیبانی نمی‌شوند، `div` پاپ‌آور را پنهان می‌کنیم تا به صورت درون‌خطی نمایش داده نشود.

```js
const instructions = document.getElementById("instructions");
const popover = document.getElementById("mypopover");

if (!Object.hasOwn(HTMLElement.prototype, "popover")) {
  popover.innerText = "";
  instructions.innerText = "پاپ‌آورها پشتیبانی نمی‌شوند";
}
```

اگر پاپ‌آورها پشتیبانی شوند، یک شنونده برای فشار دادن کلید `h` اضافه می‌کنیم و از آن برای باز کردن پاپ‌آپ استفاده می‌کنیم.
همچنین پس از فراخوانی، باز یا بسته بودن پاپ‌آپ را ثبت می‌کنیم، اما فقط در صورتی که `true` یا `false` برگردانده شده باشد.

```js
if (Object.hasOwn(HTMLElement.prototype, "popover")) {
  document.addEventListener("keydown", (event) => {
    if (event.key === "h") {
      const popupOpened = popover.togglePopover();

      // بررسی باز یا بسته بودن پاپ‌آور در مرورگرهای پشتیبانی‌کننده
      if (popupOpened !== undefined) {
        instructions.innerText +=
          popupOpened === true ? `\nباز شد` : `\nبسته شد`;
      }
    }
  });
}
```

می‌توانید این را با استفاده از مثال زنده زیر آزمایش کنید.

{{EmbedLiveSample('Examples', 700, 290)}}

## مشخصات (Specifications)

{{Specifications}}

## سازگاری مرورگر (Browser compatibility)

{{Compat}}

## همچنین ببینید (See also)

- ویژگی سراسری HTML [`popover`](/en-US/docs/Web/HTML/Reference/Global_attributes/popover)
- [Popover API](/en-US/docs/Web/API/Popover_API)
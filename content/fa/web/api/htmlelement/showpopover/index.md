---
title: "HTMLElement: showPopover() method"
---

---
title: "HTMLElement: showPopover() method"
short-title: showPopover()
slug: Web/API/HTMLElement/showPopover
page-type: web-api-instance-method
browser-compat: api.HTMLElement.showPopover
---

{{APIRef("Popover API")}}

متد **`showPopover()`** از رابط {{domxref("HTMLElement")}} یک عنصر popover (یعنی عنصری که ویژگی [`popover`](/en-US/docs/Web/HTML/Reference/Global_attributes/popover) معتبر دارد) را با افزودن آن به {{glossary("top layer", "لایه بالایی")}} نمایش می‌دهد.

هنگامی که `showPopover()` روی عنصری با ویژگی [`popover`](/en-US/docs/Web/HTML/Reference/Global_attributes/popover) که در حال حاضر پنهان است فراخوانی شود، رویداد {{domxref("HTMLElement/beforetoggle_event", "beforetoggle")}} به راه می‌افتد، سپس popover نمایش داده می‌شود و در ادامه رویداد {{domxref("HTMLElement/toggle_event", "toggle")}} رخ می‌دهد.

## نحو

```js-nolint
showPopover()
showPopover(options)
```

### پارامترها

- `options` {{optional_inline}}
  - : یک شیء که می‌تواند ویژگی‌های زیر را شامل شود:
    - `source` {{optional_inline}}
      - : یک ارجاع به {{domxref("HTMLElement")}}؛ به صورت برنامه‌نویسی عنصر فراخواننده popover مرتبط با عمل نمایش را تعریف می‌کند، یعنی عنصر کنترل آن. برقراری ارتباط بین یک popover و فراخواننده آن با استفاده از گزینه `source` دو اثر مفید دارد:
        - مرورگر هنگام نمایش، popover را در موقعیتی منطقی در ترتیب پیمایش فوکوس صفحه‌کلید قرار می‌دهد. این کار دسترسی کاربران صفحه‌کلید را به popover بهبود می‌بخشد (همچنین به [ویژگی‌های دسترسی Popover](/en-US/docs/Web/API/Popover_API/Using#popover_accessibility_features) مراجعه کنید).
        - مرورگر یک ارجاع anchor ضمنی بین این دو ایجاد می‌کند که موقعیت‌دهی popoverها را نسبت به عناصر کنترلی آن‌ها با استفاده از [موقعیت‌دهی anchor در CSS](/en-US/docs/Web/CSS/Guides/Anchor_positioning) بسیار راحت می‌سازد. برای جزئیات بیشتر به [موقعیت‌دهی anchor در Popover](/en-US/docs/Web/API/Popover_API/Using#popover_anchor_positioning) مراجعه کنید.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر این متد در حالی فراخوانی شود که یک popover دیگر در حال نمایش یا پنهان شدن است (مثلاً در داخل یک شنونده رویداد `beforetoggle`) این خطا پرتاب می‌شود.

## مثال‌ها

مثال زیر قابلیتی را فراهم می‌کند که با فشردن یک کلید خاص روی صفحه‌کلید، یک popover نمایش داده شود.

ابتدا کمی HTML:

```html
<div id="mypopover" popover>
  <h2>Help!</h2>

  <p>You can use the following commands to control the app</p>

  <ul>
    <li>Press <ins>C</ins> to order cheese</li>
    <li>Press <ins>T</ins> to order tofu</li>
    <li>Press <ins>B</ins> to order bacon</li>
  </ul>
  <hr />
  <ul>
    <li>Say "Service" to summon the robot waiter to take your order</li>
    <li>Say "Escape" to engage the ejector seat</li>
  </ul>
</div>
```

و حالا جاوااسکریپت برای اتصال این قابلیت:

```js
const popover = document.getElementById("mypopover");

document.addEventListener("keydown", (event) => {
  if (event.key === "h") {
    popover.showPopover();
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Popover API](/en-US/docs/Web/API/Popover_API)
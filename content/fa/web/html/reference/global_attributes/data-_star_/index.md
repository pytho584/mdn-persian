---
title: "data-* HTML global attributes"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/data-*"
translated_by: "n8n + AI"
---

**`data-*`** یک ویژگی سراسری (global attribute) در HTML است که گروهی از ویژگی‌ها به نام **ویژگی‌های داده سفارشی (custom data attributes)** را تشکیل می‌دهد. این ویژگی‌ها به شما امکان می‌دهند اطلاعات اختصاصی را بین HTML و DOM آن به کمک اسکریپت‌ها جابه‌جا کنید.

تمام این داده‌های سفارشی از طریق interface `HTMLElement` عنصری که ویژگی روی آن قرار دارد در دسترس هستند. property `HTMLElement.dataset` به شما دسترسی به آن‌ها را می‌دهد.

`*` را می‌توان با هر نامی که از قوانین نام‌گذاری XML پیروی می‌کند جایگزین کرد. این قوانین شامل توصیه‌های زیر است:

- نام نباید با `xml` (بدون حساسیت به بزرگی/کوچکی حروف) شروع شود، چون برای مشخصات آینده XML رزرو شده است.
- نام نباید شامل دو نقطه (`:`) باشد، چون XML به این نام‌ها معنا می‌دهد.
- نام نباید شامل حروف بزرگ باشد، چون XML همه حروف کوچک است.

این‌ها فقط توصیه هستند. اگر رعایت نشوند، خطایی رخ نمی‌دهد. ویژگی‌ها همچنان با selectors ویژگی (attribute selectors) در CSS تطبیق داده می‌شوند — ویژگی بدون حساسیت به بزرگی/کوچکی حروف و مقدار ویژگی با حساسیت به بزرگی/کوچکی حروف بررسی می‌شود. ویژگی‌هایی که این سه توصیه را رعایت نکنند نیز توسط property `HTMLElement.dataset` در JavaScript شناسایی می‌شوند و user-agent آن‌ها را در `DOMStringMap` که شامل تمام ویژگی‌های داده سفارشی برای یک `HTMLElement` است قرار می‌دهد.

اگر قصد استفاده از `HTMLElement.dataset` را دارید، بخشی از نام ویژگی که بعد از `data-` می‌آید فقط می‌تواند شامل کاراکترهایی باشد که در نام‌های property JavaScript مجاز هستند (و خط تیره که حذف می‌شود). نسخه `dataset` از نام ویژگی، پیشوند `data-` را حذف می‌کند و باقی نام را از kebab-case به camelCase تبدیل می‌کند. مثلاً `element.getAttribute("data-test")` معادل `element.dataset.test` است و `data-test-abc` به صورت `HTMLElement.dataset.testAbc` (یا `HTMLElement.dataset["testAbc"]`) قابل دسترسی خواهد بود. از کاراکترهای غیرالفبایی بعد از خط تیره مثل `data-test-1` یا `data--test` خودداری کنید، چون توسط `HTMLElement.dataset` شناسایی نمی‌شوند.

## نکات استفاده

با افزودن ویژگی‌های `data-*`، حتی عناصر معمولی HTML می‌توانند به اشیاء برنامه‌ای نسبتاً پیچیده و قدرتمند تبدیل شوند. مثلاً یک "sprite" سفینه فضایی در یک بازی می‌تواند فقط یک عنصر `<img>` با ویژگی [`class`](/en-US/docs/Web/HTML/Reference/Global_attributes/class) و چند ویژگی `data-*` باشد:

```html
<img
  class="spaceship cruiserX3"
  src="shipX3.png"
  data-ship-id="324"
  data-weapons="laserI laserII"
  data-shields="72%"
  data-x="414354"
  data-y="85160"
  data-z="31940" />
```

```markdown
```js
function clickSpaceship() {
  spaceships[this.dataset.shipId].blasted();
}

document.querySelectorAll("img.spaceship").forEach((ship) => {
  ship.addEventListener("click", clickSpaceship);
});
```

برای آموزش عمیق‌تر درباره استفاده از ویژگی‌های داده (data attributes) در HTML، به [استفاده از ویژگی‌های داده](/en-US/docs/Web/HTML/How_to/Use_data_attributes) مراجعه کنید.

## Specifications

## Browser compatibility

## See also

- همهٔ [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes).
- خاصیت `HTMLElement.dataset` که دسترسی به این مقادیر و تغییر آن‌ها را فراهم می‌کند.
- [استفاده از ویژگی‌های داده](/en-US/docs/Web/HTML/How_to/Use_data_attributes)
```
---
title: "Element: click event"
short-title: click
slug: Web/API/Element/click_event
page-type: web-api-event
browser-compat: api.Element.click_event
---

{{APIRef("UI Events")}}

یک عنصر زمانی رویداد **`click`** را دریافت می‌کند که هر یک از موارد زیر رخ دهد:

- دکمه دستگاه نشانگر (مانند دکمه اصلی ماوس) در حالی که اشاره‌گر داخل عنصر قرار دارد، هم فشرده و هم رها شود.
- یک حرکت لمسی (touch) روی عنصر انجام شود.
- هر تعامل کاربر که معادل کلیک باشد، مانند فشردن کلید <kbd>Space</kbd> یا <kbd>Enter</kbd> در حالی که عنصر فوکوس دارد. توجه داشته باشید که این فقط برای عناصری اعمال می‌شود که دارای کنترل‌کننده پیش‌فرض رویداد صفحه‌کلید هستند و بنابراین، عناصر دیگری را که با تنظیم ویژگی [`tabindex`](/en-US/docs/Web/HTML/Reference/Global_attributes/tabindex) قابل فوکوس شده‌اند، شامل نمی‌شود.

اگر دکمه روی یک عنصر فشرده شود و قبل از رها شدن دکمه، اشاره‌گر به خارج از عنصر منتقل شود، رویداد روی نزدیک‌ترین عنصر جد مشترکی که هر دو عنصر را در بر می‌گیرد، فعال می‌شود.

رویداد `click` پس از فعال شدن هر دو رویداد {{domxref("Element/mousedown_event", "mousedown")}} و {{domxref("Element/mouseup_event", "mouseup")}}، به همین ترتیب، فعال می‌شود.

این رویداد یک رویداد مستقل از دستگاه است — به این معنی که می‌تواند توسط لمس، صفحه‌کلید، ماوس و هر مکانیزم دیگری که توسط فناوری کمکی فراهم می‌شود، فعال شود.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("click", (event) => { })

onclick = (event) => { }
```

## نوع رویداد

یک {{domxref("PointerEvent")}}. از {{domxref("MouseEvent")}} به ارث می‌برد.

{{InheritanceDiagram("PointerEvent")}}

> [!NOTE]
> در نسخه‌های قبلی مشخصات، نوع رویداد برای این رویداد یک {{domxref("MouseEvent")}} بود. برای اطلاعات بیشتر به [سازگاری مرورگر](#browser_compatibility) مراجعه کنید.

## نکات استفاده

شیء {{domxref("PointerEvent")}} که به کنترل‌کننده رویداد برای `click` ارسال می‌شود، ویژگی {{domxref("UIEvent/detail", "detail")}} آن برابر با تعداد دفعاتی است که {{domxref("Event.target", "target")}} کلیک شده است. به عبارت دیگر، `detail` برای دابل‌کلیک عدد ۲، برای تریپل‌کلیک عدد ۳ و غیره خواهد بود. این شمارنده پس از یک فاصله زمانی کوتاه بدون هیچ کلیکی بازنشانی می‌شود؛ مدت زمان دقیق این فاصله ممکن است در مرورگرهای مختلف و پلتفرم‌های مختلف متفاوت باشد. این فاصله همچنین احتمالاً تحت تأثیر تنظیمات کاربر قرار می‌گیرد؛ به عنوان مثال، گزینه‌های دسترس‌پذیری ممکن است این فاصله را افزایش دهند تا انجام چندین کلیک با رابط‌های تطبیقی آسان‌تر شود.

## مثال‌ها

این مثال تعداد کلیک‌های متوالی روی یک {{HtmlElement("button")}} را نمایش می‌دهد.

### HTML

```html
<button>Click</button>
```

### JavaScript

```js
const button = document.querySelector("button");

button.addEventListener("click", (event) => {
  button.textContent = `Click count: ${event.detail}`;
});
```

### نتیجه

سعی کنید کلیک‌های سریع و مکرر روی دکمه انجام دهید تا تعداد کلیک افزایش یابد. اگر بین کلیک‌ها مکث کنید، شمارنده بازنشانی می‌شود.

{{EmbedLiveSample("Examples")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [یادگیری: مقدمه‌ای بر رویدادها](/en-US/docs/Learn_web_development/Core/Scripting/Events)
- {{domxref("Element/auxclick_event", "auxclick")}}
- {{domxref("Element/contextmenu_event", "contextmenu")}}
- {{domxref("Element/dblclick_event", "dblclick")}}
- {{domxref("Element/mousedown_event", "mousedown")}}
- {{domxref("Element/mouseup_event", "mouseup")}}
- {{domxref("Element/pointerdown_event", "pointerdown")}}
- {{domxref("Element/pointerup_event", "pointerup")}}
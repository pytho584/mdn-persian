---
title: "<marquee> HTML marquee element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/marquee"
translated_by: "n8n + AI"
---

المان `<marquee>` در HTML برای ایجاد یک ناحیهٔ متحرک (اسکرول‌شونده) از متن استفاده می‌شود. با استفاده از attribute های این المان می‌توانید رفتار متن را وقتی به لبه‌های ناحیهٔ محتوا می‌رسد کنترل کنید.

المان `<marquee>` منسوخ (deprecated) شده است و استفاده از آن به‌شدت توصیه نمی‌شود. اگر باید افکت اسکرول متن یا حرکت مداوم المان‌ها را ایجاد کنید، به‌جای استفاده از المان `<marquee>`، از [CSS animations](/en-US/docs/Web/CSS/Guides/Animations) همراه با [CSS transforms](/en-US/docs/Web/CSS/Guides/Transforms/Using) استفاده کنید تا محتوا به‌نرمی انیمیت شود. همچنین کوئری `@media (prefers-reduced-motion)` را اضافه کنید تا انیمیشن بر اساس ترجیح کاربر متوقف شود؛ این کار تجربهٔ کاربری و دسترس‌پذیری را بهبود می‌بخشد.

## Attribute ها

- `behavior`
  - : مشخص می‌کند که متن داخل marquee چگونه اسکرول شود. مقادیر ممکن عبارت‌اند از `scroll`، `slide` و `alternate`. اگر مقداری مشخص نشود، مقدار پیش‌فرض `scroll` است.
- `bgcolor`
  - : رنگ پس‌زمینه را با نام رنگ یا مقدار هگزادسیمال (hexadecimal) تعیین می‌کند.
- `direction`
  - : جهت اسکرول متن داخل marquee را مشخص می‌کند. مقادیر ممکن عبارت‌اند از `left`، `right`، `up` و `down`. اگر مقداری مشخص نشود، مقدار پیش‌فرض `left` است.
- `height`
  - : ارتفاع را بر حسب پیکسل یا درصد تعیین می‌کند.
- `hspace`
  - : حاشیهٔ افقی را تعیین می‌کند.
- `loop`
  - : تعداد دفعات اسکرول marquee را مشخص می‌کند. اگر مقداری مشخص نشود، مقدار پیش‌فرض ۱− است؛ یعنی marquee به‌صورت پیوسته اسکرول می‌شود.
- `scrollamount`
  - : مقدار جابه‌جایی در هر بازهٔ اسکرول را بر حسب پیکسل تعیین می‌کند. مقدار پیش‌فرض ۶ است.
- `scrolldelay`
  - : فاصلهٔ بین هر حرکت اسکرول را بر حسب میلی‌ثانیه مشخص می‌کند. مقدار پیش‌فرض ۸۵ است. توجه داشته باشید که اگر `truespeed` مشخص نشده باشد، هر مقدار کمتر از ۶۰ نادیده گرفته می‌شود و به‌جای آن از ۶۰ استفاده می‌شود.
- `truespeed`
  - : به‌طور پیش‌فرض، مقادیر `scrolldelay` کمتر از ۶۰ نادیده گرفته می‌شوند. اگر `truespeed` وجود داشته باشد، این مقادیر نادیده گرفته نمی‌شوند.
- `vspace`
  - : حاشیهٔ عمودی را بر حسب پیکسل یا درصد تعیین می‌کند.
- `width`
  - : عرض را بر حسب پیکسل یا درصد تعیین می‌کند.

## مثال‌ها

```html
<marquee>This text will scroll from right to left</marquee>

<marquee direction="up">This text will scroll from bottom to top</marquee>

<marquee
  direction="down"
  width="250"
  height="200"
  behavior="alternate"
  class="outlined">
  <marquee behavior="alternate">This text will bounce</marquee>
</marquee>
```

```css
.outlined {
  border: solid;
}
```

### نتیجه

خروجی نمونه‌های بالا، متن‌هایی هستند که بسته به attribute های تنظیم‌شده، در جهت‌های مختلف حرکت می‌کنند.

## خلاصهٔ فنی

| | |
| --- | --- |
| رابط DOM | `HTMLMarqueeElement` |

## همچنین ببینید

- ویژگی CSS `transform`
- ویژگی CSS `translate`
- ماژول [CSS transforms](/en-US/docs/Web/CSS/Guides/Transforms)
- ماژول [CSS animations](/en-US/docs/Web/CSS/Guides/Animations)
- `HTMLMarqueeElement`
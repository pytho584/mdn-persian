---
title: CSS Painting API
slug: Web/API/CSS_Painting_API
page-type: web-api-overview
status:
  - experimental
browser-compat: api.PaintWorkletGlobalScope
---

{{DefaultAPISidebar("CSS Painting API")}}{{SeeCompatTable}}

**CSS Painting API** — بخشی از چتر APIهای [CSS Houdini](/en-US/docs/Web/API/Houdini_APIs) — به توسعه‌دهندگان اجازه می‌دهد توابع جاوااسکریپتی بنویسند که مستقیماً در پس‌زمینه، حاشیه یا محتوای یک عنصر رسم کنند.

## مفاهیم و کاربرد

به طور خلاصه، CSS Painting API شامل قابلیت‌هایی است که به توسعه‌دهندگان امکان می‌دهد مقادیر سفارشی برای {{cssxref('image/paint', 'paint()')}}، یک تابع {{cssxref('&lt;image&gt;')}} در CSS، ایجاد کنند. سپس می‌توانید این مقادیر را روی ویژگی‌هایی مانند {{cssxref('background-image')}} اعمال کنید تا پس‌زمینه‌های سفارشی پیچیده‌ای برای یک عنصر تنظیم کنید.

به عنوان مثال:

```css
aside {
  background-image: paint(my-painted-image);
}
```

این API یک {{domxref('worklet')}} تعریف می‌کند که می‌تواند برای تولید برنامه‌ریزی شده یک تصویر که به تغییرات استایل محاسبه‌شده پاسخ می‌دهد، استفاده شود. برای اطلاعات بیشتر در مورد نحوه استفاده از آن، به [استفاده از CSS Painting API](/en-US/docs/Web/API/CSS_Painting_API/Guide) مراجعه کنید.

## رابط‌ها

- {{domxref('PaintWorkletGlobalScope')}}
  - : زمینه اجرای جهانی worklet نقاشی.
- {{domxref('PaintRenderingContext2D')}}
  - : زمینه رندرینگ برای زمینه رندرینگ CSS Painting API جهت رسم روی بیت‌مپ.
- {{domxref('PaintSize')}}
  - : اندازه بیت‌مپ خروجی که نویسنده باید روی آن رسم کند را نشان می‌دهد.

## مثال‌ها

مثال زیر یک لیست از موارد دارای تصویر پس‌زمینه ایجاد می‌کند که بین سه رنگ و سه عرض مختلف چرخش می‌کند.
در [مرورگر پشتیبانی‌کننده](#browser_compatibility) تصویری مشابه تصویر زیر خواهید دید.

![عرض و رنگ تصویر پس‌زمینه بر اساس ویژگی‌های سفارشی تغییر می‌کند](Guide/boxbg.png)

برای رسیدن به این هدف، دو ویژگی سفارشی CSS، `--box-color` و `--width-subtractor` را تعریف می‌کنیم.

### worklet نقاشی

worklet یک فایل جاوااسکریپت خارجی است (در این مورد آن را `boxbg.js` نامیده‌ایم) که یک {{domxref('worklet')}} نقاشی تعریف می‌کند.
با استفاده از worklet، می‌توانیم به ویژگی‌های CSS (و ویژگی‌های سفارشی) عناصر دسترسی پیدا کنیم:

```js
registerPaint(
  "boxbg",
  class {
    static get contextOptions() {
      return { alpha: true };
    }
    /*
      هر ویژگی سفارشی (یا ویژگی معمولی،
      مانند 'height') که برای عنصر تعریف شده است را بازیابی کرده
      و به عنوان یک آرایه بازمی‌گرداند.
    */
    static get inputProperties() {
      return ["--box-color", "--width-subtractor"];
    }

    paint(ctx, size, props) {
      /*
        ctx -> زمینه رسم
        size -> paintSize: عرض و ارتفاع
        props -> ویژگی‌ها: متد get()
      */
      ctx.fillStyle = props.get("--box-color");
      ctx.fillRect(
        0,
        size.height / 3,
        size.width * 0.4 - props.get("--width-subtractor"),
        size.height * 0.6,
      );
    }
  },
);
```

ما از متد `inputProperties()` در کلاس `registerPaint()` برای دریافت مقادیر دو ویژگی سفارشی تنظیم شده روی عنصری که `boxbg` به آن اعمال شده است استفاده کردیم و سپس آن‌ها را در تابع `paint()` خود به کار بردیم. متد `inputProperties()` می‌تواند تمام ویژگی‌های تأثیرگذار بر عنصر را بازگرداند، نه فقط ویژگی‌های سفارشی را.

### استفاده از worklet نقاشی

#### HTML

```html live-sample___example-boxbg
<ul>
  <li>مورد ۱</li>
  <li>مورد ۲</li>
  <li>مورد ۳</li>
  <li>مورد ۴</li>
  <li>مورد ۵</li>
  <li>مورد ۶</li>
  <li>مورد ۷</li>
  <li>مورد ۸</li>
  <li>مورد ۹</li>
  <li>مورد ۱۰</li>
  <li>مورد N</li>
</ul>
```

#### CSS

در CSS خود، ویژگی‌های سفارشی `--box-color` و `--width-subtractor` را تعریف می‌کنیم.

```css live-sample___example-boxbg
body {
  font: 1.2em / 1.2 sans-serif;
}
li {
  background-image: paint(boxbg);
  --box-color: hsl(55 90% 60%);
}

li:nth-of-type(3n) {
  --box-color: hsl(155 90% 60%);
  --width-subtractor: 20;
}

li:nth-of-type(3n + 1) {
  --box-color: hsl(255 90% 60%);
  --width-subtractor: 40;
}
```

#### JavaScript

راه‌اندازی و منطق worklet نقاشی در اسکریپت خارجی قرار دارد.
برای ثبت worklet، باید {{domxref('Worklet.addModule', 'addModule()')}} را از اسکریپت اصلی خود فراخوانی کنیم:

```js live-sample___example-boxbg
CSS.paintWorklet.addModule(
  "https://mdn.github.io/houdini-examples/cssPaint/intro/worklets/boxbg.js",
);
```

در این مثال، worklet در `https://mdn.github.io/` میزبانی می‌شود، اما worklet شما می‌تواند یک منبع نسبی مانند زیر باشد:

```js
CSS.paintWorklet.addModule("boxbg.js");
```

#### نتیجه

اگرچه نمی‌توانید با اسکریپت worklet بازی کنید، می‌توانید مقادیر ویژگی‌های سفارشی را در DevTools تغییر دهید تا رنگ‌ها و عرض تصویر پس‌زمینه را تغییر دهید.

{{EmbedLiveSample("example-boxbg", "", "300px")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از CSS Painting API](/en-US/docs/Web/API/CSS_Painting_API/Guide)
- [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Typed_OM_API)
- [Houdini APIs](/en-US/docs/Web/API/Houdini_APIs)
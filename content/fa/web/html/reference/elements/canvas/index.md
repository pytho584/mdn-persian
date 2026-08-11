---
title: "<canvas> HTML graphics canvas element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/canvas"
translated_by: "n8n + AI"
---

از عنصر **`<canvas>` HTML** همراه با [canvas scripting API](/en-US/docs/Web/API/Canvas_API) یا [WebGL API](/en-US/docs/Web/API/WebGL_API) برای رسم گرافیک و انیمیشن استفاده کنید.

## ویژگی‌ها

ویژگی‌های این عنصر شامل [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) می‌شود.

- `height`
  - : ارتفاع فضای مختصات بر حسب پیکسل‌های CSS. پیش‌فرض: ۱۵۰.
- `moz-opaque` (غیراستاندارد) (منسوخ)
  - : به canvas اطلاع می‌دهد که آیا شفافیت (translucency) عاملی خواهد بود یا نه. اگر canvas بداند که شفافیت وجود ندارد، می‌تواند عملکرد ترسیم را بهینه کند. این ویژگی فقط در مرورگرهای مبتنی بر Mozilla پشتیبانی می‌شود؛ به جای آن از روش استانداردشدهٔ [canvas.getContext('2d', { alpha: false })](/en-US/docs/Web/API/HTMLCanvasElement/getContext) استفاده کنید.
- `width`
  - : عرض فضای مختصات بر حسب پیکسل‌های CSS. پیش‌فرض: ۳۰۰.

## نکات استفاده

### محتوای جایگزین

باید محتوای جایگزین (alternate content) را داخل بلوک `<canvas>` قرار دهید. این محتوا هم در مرورگرهای قدیمی که canvas را پشتیبانی نمی‌کنند و هم در مرورگرهایی که جاوااسکریپت غیرفعال است، نمایش داده می‌شود.

### تگ پایانی `</canvas>`

برخلاف عنصر `<img>`، عنصر `<canvas>` **نیازمند** تگ بسته‌شدن (`</canvas>`) است.

### تنظیم اندازه canvas با CSS در برابر HTML

اندازهٔ نمایش‌داده‌شدهٔ canvas را می‌توان با CSS تغییر داد، اما اگر چنین کنید، تصویر هنگام رندر برای مطابقت با اندازهٔ استایل‌شده مقیاس می‌شود و در نتیجه ممکن است خروجی نهایی گرافیک اعوجاج یابد.

بهتر است ابعاد canvas را با تنظیم attributeهای `width` و `height` به‌طور مستقیم روی عناصر `<canvas>` تعیین کنید؛ یا مستقیماً در HTML یا با استفاده از JavaScript.

### حداکثر اندازهٔ canvas

حداکثر اندازهٔ دقیق عنصر `<canvas>` به مرورگر و محیط بستگی دارد. هرچند در بیشتر موارد ابعاد حداکثر بیش از ۱۰٬۰۰۰ × ۱۰٬۰۰۰ پیکسل است، اما به‌ویژه دستگاه‌های iOS اندازهٔ canvas را تنها به ۴٬۰۹۶ × ۴٬۰۹۶ پیکسل محدود می‌کنند. رجوع کنید به [محدودیت‌های اندازهٔ canvas در مرورگرها و دستگاه‌های مختلف](https://jhildenbiddle.github.io/canvas-size/#/?id=test-results).

> [!NOTE]
> تجاوز از حداکثر ابعاد یا مساحت، canvas را غیرقابل‌استفاده می‌کند — دستورات رسم کار نخواهند کرد.

### استفاده از canvas خارج از صفحه

یک canvas را می‌توان با استفاده از API مربوط به [OffscreenCanvas](/en-US/docs/Web/API/OffscreenCanvas) رندر کرد، به‌گونه‌ای که سند و canvas از یکدیگر جدا شوند. مزیت این کار این است که یک [worker thread](/en-US/docs/Web/API/Web_Workers_API/Using_web_workers) می‌تواند رندر canvas را انجام دهد و main thread برنامهٔ وب شما توسط عملیات canvas مسدود نمی‌شود. با موازی‌سازی کارها، سایر عناصر رابط کاربری برنامهٔ وب شما واکنش‌پذیر باقی می‌مانند، حتی اگر در حال اجرای گرافیک‌های پیچیده روی یک canvas خارج از صفحه باشید. برای اطلاعات بیشتر، مستندات API مربوط به `OffscreenCanvas` را ببینید.

## دسترس‌پذیری

### محتوای جایگزین

عنصر `<canvas>` به خودی خود فقط یک bitmap است و اطلاعاتی دربارهٔ اشیاء رسم‌شده ارائه نمی‌دهد. محتوای canvas مانند HTML معنایی (semantic HTML) در اختیار ابزارهای دسترس‌پذیری قرار نمی‌گیرد. به‌طور کلی، باید از به‌کارگیری canvas در وب‌سایت یا برنامه‌های قابل‌دسترس خودداری کنید. راهنماهای زیر می‌توانند به دسترس‌پذیرتر کردن آن کمک کنند.

- [Canvas accessibility use cases](https://www.w3.org/WAI/PF/HTML/wiki/Canvas_Accessibility_Use_Cases)
- [Canvas element accessibility issues](https://www.w3.org/html/wg/wiki/AddedElementCanvas)
- [Best practices for interactive canvas elements](https://html.spec.whatwg.org/multipage/scripting.html#best-practices)

## نمونه‌ها

### HTML

این قطعه کد یک عنصر canvas را به سند HTML شما اضافه می‌کند. اگر مرورگری قادر به خواندن یا رندر کردن canvas نباشد، یک متن جایگزین ارائه می‌شود.

```html
<canvas width="120" height="120">
  An alternative text describing what your canvas displays.
</canvas>
```

### جاوااسکریپت

سپس در کد جاوااسکریپت، با فراخوانی `{{domxref("HTMLCanvasElement.getContext()")}}` یک context رسم (drawing context) دریافت می‌کنید و شروع به رسم روی canvas می‌کنید:

```js
const canvas = document.querySelector("canvas");
const ctx = canvas.getContext("2d");
ctx.fillStyle = "green";
// یک مستطیل در موقعیت (10, 10) با اندازه 100×100 پیکسل اضافه می‌کند
ctx.fillRect(10, 10, 100, 100);
```

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories"
          >دسته‌بندی محتوا</a
        >
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content"
          >محتوا جریانی</a
        >،
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content"
          >محتوا عبارتی</a
        >،
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#embedded_content"
          >محتوا جاسازی‌شده</a
        >، محتوای قابل لمس.
      </td>
    </tr>
    <tr>
      <th scope="row">محتوا مجاز</th>
      <td>
        شفاف اما بدون فرزندان
        <a
          href="/en-US/docs/Web/HTML/Guides/Content_categories#interactive_content"
          >محتوا تعاملی</a
        >، به جز عناصر <code>&lt;a&gt;</code>، <code>&lt;button&gt;</code> و عناصر <code>&lt;input&gt;</code> که ویژگی <code>type</code> آنها <code>checkbox</code>، <code>radio</code> یا <code>button</code> باشد.
      </td>
    </tr>
    <tr>
      <th scope="row">حذف برچسب</th>
      <td>هیچ‌کدام؛ هر دو برچسب شروع و پایان اجباری هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز</th>
      <td>
        هر عنصری که
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content"
          >محتوا عبارتی</a
        > را می‌پذیرد.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td>
        <a href="https://w3c.github.io/html-aria/#dfn-no-corresponding-role"
          >بدون نقش متناظر</a
        >
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>هر نوع</td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td><code>HTMLCanvasElement</code></td>
    </tr>
  </tbody>
</table>

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Canvas API](/en-US/docs/Web/API/Canvas_API)
- [آموزش Canvas](/en-US/docs/Web/API/Canvas_API/Tutorial)
- [OffscreenCanvas](/en-US/docs/Web/API/OffscreenCanvas)
- [برگه تقلب Canvas](https://simon.html5.org/dump/html5-canvas-cheat-sheet.html) (2009)
- [برگه تقلب Canvas](https://websitesetup.org/wp-content/uploads/2015/11/Infopgraphic-CanvasCheatSheet-Final2.pdf) (pdf) (2015)
- [راهنمای Canvas مرورگر Safari](https://developer.apple.com/library/archive/documentation/AudioVideo/Conceptual/HTML-canvas-guide/Introduction/Introduction.html) از Apple (2013)
- [`CanvasRenderingContext2D` — context رسم دو بعدی برای عنصر canvas](https://developer.apple.com/documentation/webkitjs/canvasrenderingcontext2d) از Apple.com
- [API WebGL](/en-US/docs/Web/API/WebGL_API)
- {{HTMLElement("img")}}
- [SVG](/en-US/docs/Web/SVG)
- [ویدئو و صدا در HTML](/en-US/docs/Learn_web_development/Core/Structuring_content/HTML_video_and_audio)
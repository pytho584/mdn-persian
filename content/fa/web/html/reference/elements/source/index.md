---
title: "<source> HTML media or image source element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/source"
translated_by: "n8n + AI"
---

# عنصر `<source>` — منبع رسانه یا تصویر HTML

**`<source>`** یک [HTML](/en-US/docs/Web/HTML) element است که یک یا چند منبع رسانه را برای عنصرهای `picture`، `audio` و `video` مشخص می‌کند. این یک `void element` است؛ یعنی محتوایی ندارد و به تگ بسته نیاز ندارد. از این element معمولاً برای ارائهٔ همان محتوای رسانه در چند فرمت فایل استفاده می‌شود تا با مرورگرهای مختلف، با توجه به پشتیبانی متفاوتشان از [image file formats](/en-US/docs/Web/Media/Guides/Formats/Image_types) و [media file formats](/en-US/docs/Web/Media/Guides/Formats/Containers)، سازگاری ایجاد کند.

```html interactive-example
<video controls width="250" height="200" muted>
  <source src="/shared-assets/videos/flower.webm" type="video/webm" />
  <source src="/shared-assets/videos/flower.mp4" type="video/mp4" />
  Download the
  <a href="/shared-assets/videos/flower.webm">WEBM</a>
  or
  <a href="/shared-assets/videos/flower.mp4">MP4</a>
  video.
</video>
```

## Attributes

این element از تمام [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes) پشتیبانی می‌کند. علاوه بر آن، attributeهای زیر را می‌توان با آن استفاده کرد:

- `type`
  - : نوع [MIME رسانهٔ تصویر](/en-US/docs/Web/Media/Guides/Formats/Image_types) یا [نوع رسانهٔ دیگر](/en-US/docs/Web/Media/Guides/Formats/Containers) را مشخص می‌کند و می‌تواند به‌صورت اختیاری شامل [`codecs` parameter](/en-US/docs/Web/Media/Guides/Formats/codecs_parameter) باشد.

- `src`
  - : آدرس URL منبع رسانه را مشخص می‌کند. اگر والد `<source>` عنصر `audio` یا `video` باشد، این attribute الزامی است. اگر والد `picture` باشد، نباید استفاده شود.

- `srcset`
  - : فهرستی از یک یا چند URL تصویر و توصیفگرهای (descriptor) آن‌ها را مشخص می‌کند که با کاما از هم جدا شده‌اند. اگر والد `<source>` عنصر `picture` باشد، الزامی است و اگر والد `audio` یا `video` باشد، مجاز نیست.

    فهرست شامل رشته‌هایی است که با کاما از هم جدا شده‌اند و مجموعه‌ای از تصاویر ممکن را برای استفادهٔ مرورگر مشخص می‌کنند. هر رشته از این بخش‌ها تشکیل شده است:

    - یک URL که محل تصویر را مشخص می‌کند.
    - یک توصیفگر عرض اختیاری — یک عدد صحیح مثبت که بلافاصله با `"w"` همراه است، مثل `300w`.
    - یک توصیفگر تراکم پیکسل اختیاری — یک عدد اعشاری مثبت که بلافاصله با `"x"` همراه است، مثل `2x`.

    هر رشته در فهرست باید یا توصیفگر عرض داشته باشد یا توصیفگر تراکم پیکسل تا معتبر باشد. این دو توصیفگر نباید با هم استفاده شوند؛ فقط یکی از آن‌ها باید به‌صورت یکسان در کل فهرست به کار رود. مقدار هر توصیفگر در فهرست باید یکتا باشد. مرورگر بر اساس این توصیفگرها، در هر لحظه مناسب‌ترین تصویر را برای نمایش انتخاب می‌کند. اگر توصیفگرها مشخص نشده باشند، مقدار پیش‌فرض `1x` استفاده می‌شود. اگر attribute `sizes` نیز وجود داشته باشد، هر رشته باید شامل توصیفگر عرض باشد. اگر مرورگر از `srcset` پشتیبانی نکند، از `src` به‌عنوان منبع تصویر پیش‌فرض استفاده می‌شود.

- `sizes`
  - : فهرستی از اندازه‌های منبع را مشخص می‌کند که عرض نهایی رندر شدهٔ تصویر را توصیف می‌کنند. اگر والد `<source>` عنصر `picture` باشد مجاز است و اگر والد `audio` یا `video` باشد مجاز نیست.

    فهرست شامل اندازه‌های منبع است که با کاما از هم جدا شده‌اند. هر اندازهٔ منبع یک جفت شرط رسانه (media condition) و طول است. مرورگر قبل از چیدمان صفحه از این اطلاعات برای انتخاب تصویری که در [`srcset`](#srcset) تعریف شده استفاده می‌کند. توجه داشته باشید که `sizes` فقط زمانی اثر می‌کند که همراه `srcset` توصیفگرهای عرض ارائه شده باشند، نه توصیفگرهای تراکم پیکسل (یعنی باید از `200w` استفاده شود نه `2x`).

- `media`
  - : [media query](/en-US/docs/Web/CSS/Guides/Media_queries) مربوط به رسانهٔ مدنظر منبع را مشخص می‌کند.

- `height`
  - : ارتفاع ذاتی تصویر را بر حسب پیکسل مشخص می‌کند. این ویژگی فقط زمانی مجاز است که والد `<source>` یک عنصر `<picture>` باشد؛ اگر والد `<audio>` یا `<video>` باشد مجاز نیست.

    مقدار `height` باید یک عدد صحیح بدون واحد باشد.

- `width`
  - : عرض ذاتی تصویر را بر حسب پیکسل مشخص می‌کند. این ویژگی فقط زمانی مجاز است که والد `<source>` یک عنصر `<picture>` باشد؛ اگر والد `<audio>` یا `<video>` باشد مجاز نیست.

    مقدار `width` باید یک عدد صحیح بدون واحد باشد.

## یادداشت‌های استفاده

عنصر `<source>` یک **void element** است؛ یعنی نه تنها محتوایی ندارد، بلکه تگ پایانی هم ندارد. به عبارت دیگر، هرگز نباید از `</source>` در HTML استفاده کنید.

مرورگر فهرست عناصر `<source>` را بررسی می‌کند تا فرمتی را پیدا کند که از آن پشتیبانی کند. اولین موردی که بتواند نمایش دهد را انتخاب می‌کند. برای هر عنصر `<source>`:

- اگر ویژگی `type` مشخص نشده باشد، مرورگر نوع رسانه را از سرور دریافت می‌کند و بررسی می‌کند که آیا می‌تواند آن را نمایش دهد. اگر نتواند، عنصر `<source>` بعدی را بررسی می‌کند.
- اگر ویژگی `type` مشخص شده باشد، مرورگر همان‌جا آن را با نوع‌های رسانه‌ای که می‌تواند نمایش دهد مقایسه می‌کند. اگر نوع پشتیبانی نشود، مرورگر از درخواست به سرور صرف‌نظر می‌کند و مستقیماً عنصر `<source>` بعدی را بررسی می‌کند.

اگر هیچ‌کدام از عناصر `<source>` منبع قابل استفاده‌ای فراهم نکنند:

- در مورد عنصر `<picture>`، مرورگر به تصویری که در فرزند `<img>` عنصر `<picture>` مشخص شده برمی‌گردد.
- در مورد عنصر `<audio>` یا `<video>`، مرورگر به نمایش محتوایی که بین تگ شروع و پایان عنصر قرار دارد برمی‌گردد.

برای اطلاعات در مورد فرمت‌های تصویری پشتیبانی‌شده توسط مرورگرها و راهنمای انتخاب فرمت مناسب، به [راهنمای فرمت و نوع فایل تصویری](/en-US/docs/Web/Media/Guides/Formats/Image_types) مراجعه کنید. برای جزئیات مربوط به انواع رسانه‌ای ویدیو و صدا، [راهنمای نوع و فرمت رسانه](/en-US/docs/Web/Media/Guides/Formats) را ببینید.

## مثال‌ها

### استفاده از ویژگی `type` با `<video>`

این مثال نشان می‌دهد که چگونه یک ویدیو را در قالب‌های مختلف ارائه دهید: WebM برای مرورگرهایی که از آن پشتیبانی می‌کنند، Ogg برای آن‌هایی که Ogg را پشتیبانی می‌کنند، و QuickTime برای مرورگرهایی که QuickTime را پشتیبانی می‌کنند. اگر عنصر `<audio>` یا `<video>` توسط مرورگر پشتیبانی نشود، به جای آن یک پیام نمایش داده می‌شود. اگر مرورگر عنصر را پشتیبانی کند ولی هیچ‌کدام از قالب‌های مشخص‌شده را پشتیبانی نکند، رویداد `error` روی عنصر `<audio>` یا `<video>` رخ می‌دهد و کنترل‌های پیش‌فرض رسانه (اگر فعال باشند) خطا را نشان می‌دهند. برای اطلاعات بیشتر درباره فرمت‌های فایل رسانه‌ای و پشتیبانی مرورگرها، به [راهنمای نوع و فرمت رسانه](/en-US/docs/Web/Media/Guides/Formats) مراجعه کنید.

```html
<video controls>
  <source src="foo.webm" type="video/webm" />
  <source src="foo.ogg" type="video/ogg" />
  <source src="foo.mov" type="video/quicktime" />
  I'm sorry; your browser doesn't support HTML video.
</video>
```

### استفاده از ویژگی `media` با `<video>`

این مثال نشان می‌دهد که چگونه یک فایل منبع جایگزین برای viewportهای عریض‌تر از یک حد مشخص ارائه دهید. وقتی محیط مرورگر کاربر شرایط `media` مشخص‌شده را برآورده کند، عنصر `<source>` مرتبط انتخاب می‌شود. سپس محتوای ویژگی `src` آن درخواست و رندر می‌شود. اگر شرایط `media` برقرار نباشد، مرورگر به سراغ عنصر `<source>` بعدی می‌رود. گزینه دوم `<source>` در کد زیر هیچ شرط `media` ندارد، بنابراین برای همه contextهای دیگر مرورگر انتخاب می‌شود.

```html
<video controls>
  <source src="foo-large.webm" media="(width >= 800px)" />
  <source src="foo.webm" />
  I'm sorry; your browser doesn't support HTML video.
</video>
```

برای مثال‌های بیشتر، مقاله «[ویدیو و صدا در HTML](/en-US/docs/Learn_web_development/Core/Structuring_content/HTML_video_and_audio)» در بخش آموزش منبع عالی‌ای است.

### استفاده از ویژگی `media` با `<picture>`

در این مثال دو عنصر `<source>` داخل `<picture>` قرار گرفته‌اند که نسخه‌های مختلفی از یک تصویر را برای زمانی که فضای موجود از عرض‌های مشخصی بیشتر می‌شود فراهم می‌کنند. اگر عرض موجود از کوچک‌ترین این عرض‌ها کمتر باشد، مرورگر به سراغ تصویری که در عنصر `<img>` مشخص شده می‌رود.

```html
<picture>
  <source srcset="mdn-logo-wide.png" media="(width >= 800px)" />
  <source srcset="mdn-logo-medium.png" media="(width >= 600px)" />
  <img src="mdn-logo-narrow.png" alt="MDN Web Docs" />
</picture>
```

در عنصر `<picture>` همیشه باید یک `<img>` با تصویر جایگزین (fallback) قرار دهید. همچنین حتماً برای دسترسی‌پذیری (accessibility) یک ویژگی `alt` اضافه کنید، مگر اینکه تصویر صرفاً تزئینی و بی‌ربط به محتوا باشد.

### استفاده از ویژگی‌های `height` و `width` با `<picture>`

در این مثال سه عنصر `<source>` به همراه ویژگی‌های `height` و `width` داخل یک عنصر `<picture>` قرار گرفته‌اند. یک [media query](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Media_queries/Using) به مرورگر اجازه می‌دهد بر اساس اندازه [viewport](https://developer.mozilla.org/en-US/docs/Glossary/Viewport) تصویر مناسب را با ویژگی‌های `height` و `width` انتخاب کند.

```html
<picture>
  <source
    srcset="landscape.png"
    media="(width >= 1000px)"
    width="1000"
    height="400" />
  <source
    srcset="square.png"
    media="(width >= 800px)"
    width="800"
    height="800" />
  <source
    srcset="portrait.png"
    media="(width >= 600px)"
    width="600"
    height="800" />
  <img
    src="fallback.png"
    alt="Image used when the browser does not support the sources"
    width="500"
    height="400" />
</picture>
```

## خلاصه فنی

| ویژگی | مقدار |
|-------|-------|
| [دسته‌بندی محتوا](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories) | هیچکدام |
| محتوای مجاز | هیچ؛ این یک عنصر void (void element) است. |
| حذف تگ | باید تگ شروع داشته باشد و نباید تگ پایان داشته باشد. |
| والدین مجاز | یک عنصر رسانه‌ای — `<audio>` یا `<video>` — و باید قبل از هر [محتوای جریان (flow content)](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#flow_content) یا عنصر `<track>` قرار گیرد. همچنین می‌تواند داخل یک عنصر `<picture>` باشد و باید قبل از عنصر `<img>` قرار گیرد. |
| نقش ARIA ضمنی | [هیچ نقش متناظری](https://w3c.github.io/html-aria/#dfn-no-corresponding-role) |
| نقش‌های ARIA مجاز | هیچ `role` مجاز نیست |
| رابط DOM | `HTMLSourceElement` |

## جستارهای وابسته

- عنصر `<audio>`
- عنصر `<picture>`
- عنصر `<video>`
- [راهنمای انواع و فرمت‌های فایل تصویری](https://developer.mozilla.org/en-US/docs/Web/Media/Guides/Formats/Image_types)
- [راهنمای نوع و فرمت رسانه](https://developer.mozilla.org/en-US/docs/Web/Media/Guides/Formats)
- [عملکرد وب (Web performance)](https://developer.mozilla.org/en-US/docs/Learn_web_development/Extensions/Performance)
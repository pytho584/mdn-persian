---
title: "ARIA: img role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/img_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: img role"
short-title: img
slug: Web/Accessibility/ARIA/Reference/Roles/img_role
page-type: aria-role
spec-urls: https://w3c.github.io/aria/#img
sidebar: accessibilitysidebar
---

نقش `img` در ARIA می‌تواند برای شناسایی چندین عنصر در محتوای صفحه استفاده شود که باید به‌عنوان یک تصویر واحد در نظر گرفته شوند. این عناصر می‌توانند تصاویر، قطعه‌کدها، متن، ایموجی‌ها یا محتوای دیگری باشند که می‌توانند برای انتقال اطلاعات به‌صورت بصری ترکیب شوند.

```html
<div role="img" aria-label="Description of the overall image">
  <img src="graphic1.png" alt="" />
  <img src="graphic2.png" alt="" />
</div>
```

## توضیحات

هر مجموعه‌ای از محتوا که باید به‌عنوان یک تصویر واحد در نظر گرفته شود (که می‌تواند شامل تصاویر، ویدئو، صدا، قطعه‌کدها، ایموجی‌ها یا محتوای دیگر باشد) می‌تواند با استفاده از `role="img"` شناسایی شود.

برای انتقال زمینه به فناوری‌های کمکی، نباید به متن جایگزین (alt) تصاویر تکی تکیه کنید؛ بیشتر صفحه‌خوان‌ها عنصری که `role="img"` روی آن تنظیم شده است را مانند یک جعبه سیاه در نظر می‌گیرند و به عناصر درونی آن دسترسی نخواهند داشت. بنابراین، یک متن جایگزین توصیفی جامع برای تصویر فراهم کنید، یا در متن اطراف آن، یا با استفاده از ویژگی [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label)؛ و برای موتورهای جستجو یا کاربران بینا، ویژگی‌های `alt` را در صفحه قرار دهید تا در صورت بارگذاری نشدن تصویر نمایش داده شوند:

```html
<div role="img" aria-label="Description of the overall image">
  <img src="graphic1.png" alt="alternative text" />
  <img src="graphic2.png" alt="in case the images don't load" />
</div>
```

اگر می‌خواهید یک زیرنویس یا برچسب قابل مشاهده برای تصویر خود اضافه کنید، می‌توانید از موارد زیر استفاده کنید:

- [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) زمانی که متن یک برچسب مختصر است.
- [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby) زمانی که متن یک توصیف طولانی‌تر است.

برای مثال:

```html
<div role="img" aria-labelledby="image-1">
  …
  <p id="image-1">Text that describes the group of images.</p>
</div>
```

اگر تصویری صرفاً جنبه ارائه (نمایشی) دارد، استفاده از نقش [`presentation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role) را در نظر بگیرید.

### SVG و role="img"

اگر از تصاویر SVG جاسازی‌شده در صفحه خود استفاده می‌کنید، ایده خوبی است که `role="img"` را روی عنصر بیرونی {{SVGElement('svg')}} تنظیم کنید و به آن یک برچسب بدهید. این کار باعث می‌شود صفحه‌خوان‌ها آن را فقط به‌عنوان یک موجودیت واحد در نظر بگیرند و با استفاده از برچسب آن را توصیف کنند، به‌جای اینکه بخواهند همه گره‌های فرزند را بخوانند:

```html
<svg role="img" aria-label="Description of your SVG image">
  <!-- contents of the SVG image -->
</svg>
```

### استفاده از role="img" برای انتقال معناهای پنهان یا ضمنی

در برخی موارد، کاربران فناوری کمکی نمی‌توانند معنای محتوایی را که به روش‌های خاص، از طریق رسانه‌های خاص یا به‌صورت ضمنی بیان شده است، درک کنند. این مشکل در مورد تصاویر به‌وضوح قابل حل است (می‌توانید از ویژگی `alt` استفاده کنید)، اما در مورد محتوای ترکیبی یا برخی انواع دیگر محتوا چندان آشکار نیست و `role="img"` می‌تواند وارد عمل شود.

برای مثال، اگر از ایموجی‌ها در متن خود استفاده می‌کنید، ممکن است معنا برای کاربر بینا آشکار باشد، اما فردی که از صفحه‌خوان استفاده می‌کند ممکن است گیج شود، زیرا ایموجی‌ها یا اصلاً نمایش متنی ندارند، یا متن جایگزین ممکن است گیج‌کننده باشد و با زمینه‌ای که در آن استفاده شده است مطابقت نداشته باشد. برای مثال، کد زیر را در نظر بگیرید:

```html
<div role="img" aria-label="That cat is so cute">
  <p>&#x1F408; &#x1F602;</p>
</div>
```

`&#x1F408; &#x1F602;`، 🐈 و 😂، ارجاع‌های موجودیتی برای ایموجی‌هایی هستند که به‌صورت «گربه» و «صورت با اشک شادی» خوانده می‌شوند، اما این لزوماً معنادار نیست — معنای ضمنی احتمالاً بیشتر مانند «آن گربه خیلی ناز است» است، بنابراین ما آن را در یک `aria-label` همراه با `role="img"` قرار می‌دهیم.

این روش به نظر می‌رسد در برخی ترکیب‌های مرورگر/صفحه‌خوان به‌درستی کار می‌کند، اما برخی از آن‌ها ممکن است برچسب را دو بار بخوانند. با احتیاط استفاده کنید و به‌طور کامل آزمایش کنید.

مثال دیگری که این روش ممکن است مناسب باشد، زمانی است که از ترکیب‌های ایموجی {{Glossary("ASCII")}} استفاده می‌کنید، مانند «Table flip» افسانه‌ای:

```html
<div role="img" aria-label="Table flip">
  <p>(╯°□°）╯︵ ┻━┻</p>
</div>
```

اگر از `aria-labelledby` استفاده می‌شد، صفحه‌خوان آن را می‌خواند. در این حالت، فقط محتویات `aria-label` به کاربران صفحه‌خوان اعلام می‌شود و محتوای بی‌معنی نویسه‌ها پنهان می‌ماند، بدون نیاز به ARIA فرزندان برای پنهان‌سازی چیزها؛ اما این کار همچنین محتوای بالقوه‌ای را که ممکن است بخشی از تصویر باشد پنهان می‌کند.

### همه فرزندان، ارائه‌ای هستند

برخی از انواع اجزای رابط کاربری وجود دارند که وقتی در یک API دسترس‌پذیری پلتفرم نمایش داده می‌شوند، فقط می‌توانند متن داشته باشند. APIهای دسترس‌پذیری هیچ روشی برای نمایش عناصر معنایی موجود در یک `img` ندارند. برای مقابله با این محدودیت، مرورگرها به‌طور خودکار نقش [`presentation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role) را به همه عناصر فرزند هر عنصر `img` اعمال می‌کنند، زیرا این نقشی است که از فرزندان معنایی پشتیبانی نمی‌کند.

برای مثال، عنصر `img` زیر را در نظر بگیرید که شامل یک عنوان است.

```html
<div role="img"><h3>Title of my image</h3></div>
```

از آنجا که فرزندان `img` ارائه‌ای هستند، کد زیر معادل است:

```html
<div role="img"><h3 role="presentation">Title of my image</h3></div>
```

از دید کاربر فناوری کمکی، عنوان وجود ندارد، زیرا قطعه‌کدهای قبلی با موارد زیر در [درخت دسترس‌پذیری](/en-US/docs/Glossary/Accessibility_tree) معادل هستند:

```html
<div role="img">Title of my image</div>
```

### نقش‌ها، حالت‌ها و ویژگی‌های مرتبط WAI-ARIA

- `aria-label` یا `aria-labelledby`
  - : یک نام قابل‌دسترس الزامی است. برای عنصر HTML {{HTMLElement('img')}}، از ویژگی `alt` استفاده کنید. برای همه عناصر دیگر با نقش `img`، اگر برچسب قابل مشاهده وجود دارد از `aria-labelledby` استفاده کنید، در غیر این صورت از `aria-label` استفاده کنید.

## مثال‌ها

```html
<span role="img" aria-label="Rating: 4 out of 5 stars">
  <span>★</span>
  <span>★</span>
  <span>★</span>
  <span>★</span>
  <span>☆</span>
</span>
```

## مشخصات

{{Specifications}}

## همچنین ببینید

- عنصر {{HTMLElement('img')}}
- عنصر {{SVGElement('svg')}}
- عنصر {{HTMLElement('picture')}}
- عنصر {{HTMLElement('audio')}}
- عنصر {{HTMLElement('video')}}
- [نقش `presentation` در ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role)
- [مدل شیء دسترس‌پذیری](https://wicg.github.io/aom/spec/)
- [ARIA در HTML](https://w3c.github.io/html-aria/)
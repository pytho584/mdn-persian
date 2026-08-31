---
title: "ARIA: figure role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/figure_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: figure role"
short-title: figure
slug: Web/Accessibility/ARIA/Reference/Roles/figure_role
page-type: aria-role
spec-urls: https://w3c.github.io/aria/#figure
sidebar: accessibilitysidebar
---

نقش `figure` در ARIA می‌تواند برای شناسایی یک figure در محتوای صفحه، جایی که معناشناسی مناسب از قبل وجود ندارد، استفاده شود. یک figure معمولاً به‌عنوان یک یا چند تصویر، قطعه‌کد یا محتوای دیگری در نظر گرفته می‌شود که اطلاعات را به‌گونه‌ای متفاوت از جریان عادی متن ارائه می‌دهد.

## توضیحات

یک figure بخش قابل‌درکی از محتوا است که معمولاً شامل یک سند گرافیکی، تصاویر، قطعه‌کدها یا متن نمونه است. بخش‌های یک figure ممکن است قابل پیمایش توسط کاربر باشند. هر محتوایی که باید با هم گروه‌بندی شود و به‌عنوان یک figure در نظر گرفته شود (می‌تواند شامل تصاویر، ویدیو، صدا، قطعه‌کدها یا سایر محتوا باشد) می‌تواند با استفاده از `role="figure"` به‌عنوان figure شناسایی شود.

```html
<div role="figure" aria-labelledby="caption">
  <img src="image.png" alt="put image description here" />
  <p id="caption">Figure 1: The caption</p>
</div>
```

در مثال بالا، ما یک figure داریم که شامل دو آیتم محتوایی جداگانه است — یک تصویر و یک عنوان. این محتوا توسط یک عنصر {{htmlelement("div")}} که با استفاده از `role="figure"` محتوا را به‌عنوان figure شناسایی می‌کند، احاطه شده است.

برای HTML، از عناصر {{HTMLElement('figure')}} و {{HTMLElement('figcaption')}} استفاده کنید. عنصر figcaption به‌عنوان نام دسترس‌پذیر برای figure عمل می‌کند. هنگام عدم استفاده از HTML یا بازسازی HTML قدیمی، از [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) روی figure استفاده کنید که به زیرنویس figure اشاره کند. اگر زیرنویس قابل مشاهده وجود نداشته باشد، می‌توان از [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) استفاده کرد.

```html
<div role="figure" aria-labelledby="figure-1">
  …
  <p id="figure-1">Text that describes the figure.</p>
</div>
```

- وقتی متن یک برچسب مختصر است از `aria-labelledby` استفاده کنید.
- وقتی متن یک توصیف طولانی‌تر است از `aria-describedby` استفاده کنید.
- وقتی هیچ زیرنویس قابل مشاهده‌ای برای figure وجود ندارد از `aria-label` استفاده کنید.

این کار را می‌توان از لحاظ معنایی، بدون ARIA، با عنصر {{HTMLElement('figure')}} در HTML همراه با {{HTMLElement('figcaption')}} انجام داد.

```html
<figure>
  <img src="image.png" alt="put image description here" />
  <figcaption>Figure 1: The caption</figcaption>
</figure>
```

> [!NOTE]
> در صورت امکان در کار خود، باید از عناصر معنایی HTML مناسب برای نشانه‌گذاری figure و زیرنویس آن استفاده کنید — {{htmlelement("figure")}} و {{htmlelement("figcaption")}}.

### نقش‌ها، حالت‌ها و ویژگی‌های مرتبط WAI-ARIA

- [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby)
  - : شناسه (id) عنصری که شامل متن مرجع به‌عنوان زیرنویس است.
- [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby)
  - : شناسه (id) عنصری که شامل متن به‌عنوان برچسب است.
- [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label)
  - : اگر عنصری حاوی متنی که بتواند به‌عنوان برچسب باشد وجود نداشته باشد، می‌توانید برچسب را مستقیماً به‌عنوان مقدار `aria-label` روی عنصر با نقش `figure` یا روی عنصر `<figure>` اضافه کنید.

### تعاملات صفحه‌کلید

هیچ تعامل صفحه‌کلید خاصی برای این نقش وجود ندارد.

### ویژگی‌های جاوااسکریپت موردنیاز

هیچ الزام جاوااسکریپت خاصی برای این نقش وجود ندارد. اگر کنترلی بر معنای HTML ندارید، می‌توانید با افزودن این نقش‌ها و ویژگی‌ها با جاوااسکریپت، دسترس‌پذیری HTML را بهبود بخشید.

## مثال‌ها

می‌توانیم مثال ابتدایی صفحه را گسترش دهیم تا پاراگرافی را که برچسب توصیفی برای figure فراهم می‌کند با ارجاع به شناسه آن در `aria-labelledby` شناسایی کند:

```html
<div role="figure" aria-labelledby="figure-1">
  <img
    src="diagram.png"
    alt="diagram showing the four layers of awesome and their relative priority order —
        music, cats, nature, and ice cream" />
  <pre>
`
        let awesome = ['music', 'cats', 'nature', 'ice cream'];
      `</pre>
  <p id="figure-1">Figure 1: The four layers of awesome.</p>
</div>
```

## بهترین روش‌ها

فقط در صورت نیاز از `role="figure"` استفاده کنید — برای مثال، اگر کنترلی بر HTML خود ندارید اما می‌توانید دسترس‌پذیری را به‌صورت پویا و پس از آن با جاوااسکریپت بهبود بخشید.

در صورت امکان، باید از عناصر معنایی HTML مناسب برای نشانه‌گذاری figure و زیرنویس آن استفاده کنید — {{htmlelement("figure")}} و {{htmlelement("figcaption")}}. برای مثال، مثال بالا باید به صورت زیر بازنویسی شود:

```html
<figure>
  <img
    src="diagram.png"
    alt="diagram showing the four layers of awesome and their relative priority order —
         music, cats, nature, and ice cream" />
  <pre>
`
    let awesome = ['music', 'cats', 'nature', 'ice cream'];
  `</pre>
  <figcaption>Figure 1: The four layers of awesome.</figcaption>
</figure>
```

## مشخصات

{{Specifications}}

## همچنین ببینید

- [Accessibility Object Model](https://wicg.github.io/aom/spec/)
- [ARIA in HTML](https://w3c.github.io/html-aria/)
- [HTML `<figure>` element](/en-US/docs/Web/HTML/Reference/Elements/figure)
- [HTML `<figcaption>` element](/en-US/docs/Web/HTML/Reference/Elements/figcaption)
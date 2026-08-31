---
title: "ARIA: presentation role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: presentation role"
short-title: presentation
slug: Web/Accessibility/ARIA/Reference/Roles/presentation_role
page-type: aria-role
spec-urls: https://w3c.github.io/aria/#presentation
sidebar: accessibilitysidebar
---

نقش `presentation` و مترادف آن `none`، معنای ضمنی ARIA یک عنصر را از قرار گرفتن در درخت دسترس‌پذیری حذف می‌کنند.

محتوای عنصر همچنان برای فناوری‌های کمکی در دسترس خواهد بود؛ فقط معنای ظرف — و در برخی موارد، عناصر فرعی مرتبط الزامی — دیگر نگاشت خود را به API دسترس‌پذیری افشا نمی‌کنند.

## توضیحات

در حالی که ARIA عمدتاً برای بیان معنای عناصر استفاده می‌شود، برخی موقعیت‌ها وجود دارند که پنهان کردن معنای یک عنصر از فناوری‌های کمکی مفید است. این کار با نقش `presentation` یا نقش مترادف آن `none` انجام می‌شود که اعلام می‌کنند عنصر فقط برای ارائه (نمایش) استفاده شده و بنابراین هیچ معنای دسترس‌پذیری ندارد.

نوشتن `<h2 role="presentation">Democracy Dies in Darkness</h2>` معنای عنوان عنصر {{HTMLElement("Heading_Elements", "h2")}} را حذف می‌کند و آن را معادل `<div>Democracy Dies in Darkness</div>` می‌سازد. معنای نقش عنوان حذف شده، اما خود محتوا همچنان در دسترس است.

هنگامی که یک عنصر دارای عناصر فرعی الزامی است، مانند عناصر مختلف {{HTMLElement('table')}} و فرزندان {{HTMLElement('li')}} از {{HTMLElement('ul')}} یا {{HTMLElement('ol')}}، نقش `presentation` یا `none` روی جدول یا فهرست، معنای پیش‌فرض عنصر مورد نظر و عناصر فرعی الزامی آن را حذف می‌کند.

اگر `presentation` یا `none` روی عنصر {{HTMLElement('table')}} اعمال شود، عناصر فرعی {{HTMLElement('caption')}}، {{HTMLElement('thead')}}، {{HTMLElement('tbody')}}، {{HTMLElement('tfoot')}}، {{HTMLElement('tr')}}، {{HTMLElement('th')}} و {{HTMLElement('td')}} این نقش را به ارث می‌برند و بنابراین در معرض فناوری‌های کمکی قرار نمی‌گیرند. اما عناصر داخل عناصر {{HTMLElement('th')}} و {{HTMLElement('td')}}، از جمله جدول‌های تو در تو، در معرض فناوری‌های کمکی قرار می‌گیرند.

```html
<ul role="presentation">
  <li>
    <a href="#">Link 1</a>
  </li>
  <li>
    <a href="#">Link 2</a>
  </li>
  <li>
    <a href="#">Link 3</a>
  </li>
</ul>
```

از آنجا که نقش `presentation` روی عنصر {{HTMLElement('ul')}} اعمال شده، هر عنصر فرزند {{HTMLElement('li')}} این نقش را به ارث می‌برد. این به این دلیل است که ARIA ایجاب می‌کند عناصر `listitem` دارای عنصر والد `list` باشند. در این مورد، عناصر {{HTMLElement('li')}} در معرض فناوری‌های کمکی قرار نمی‌گیرند، اما فرزندان این عناصر الزامی در معرض قرار می‌گیرند. اگر یک فهرست را درون یکی از آن عناصر {{HTMLElement('li')}} تودرتو کرده بودیم، برای فناوری‌های کمکی قابل مشاهده می‌بود. برای عناصری که فرزندان الزامی ندارند، هر عنصری که درون عنصر با `role="presentation"` یا `role="none"` تودرتو شده باشد، معنای خود را حفظ می‌کند. در این مورد، عناصر {{HTMLElement('a')}} که درون آن عناصر {{HTMLElement('li')}} قرار دارند، در معرض قرار می‌گیرند.

عنصر {{HTMLElement('a')}} یک مورد خاص است. نقش آن حتی اگر نقش `presentation` یا `none` مستقیماً روی آن اعمال شده باشد، در معرض قرار می‌گرفت. مرورگرها `role="presentation"` و `role="none"` را روی عناصر قابل تمرکز، از جمله پیوندها و ورودی‌ها، یا هر چیزی با ویژگی [tabindex](/en-US/docs/Web/HTML/Reference/Global_attributes/tabindex) نادیده می‌گیرند. مرورگرها همچنین در صورتی که عنصر دارای هر گونه حالت یا ویژگی سراسری ARIA باشد، مانند [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby)، این نقش را نادیده می‌گیرند.

> [!NOTE]
> عنصر با `role="presentation"` بخشی از درخت دسترس‌پذیری نیست و نباید نام دسترس‌پذیر داشته باشد. از [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) یا [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) استفاده **نکنید**.

### نقش‌ها، حالت‌ها و ویژگی‌های مرتبط WAI-ARIA

هیچ‌کدام. اگر یک حالت یا ویژگی سراسری ARIA تنظیم شده باشد، `presentation` یا `none` نادیده گرفته می‌شود و نقش ضمنی عنصر استفاده خواهد شد.

## مثال‌ها

```html
<hr role="none" />
```

## مشخصات

{{Specifications}}

## همچنین ببینید

- [`aria-hidden`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-hidden) در مقایسه با [`role="presentation/none"`](https://www.scottohara.me/blog/2018/05/05/hidden-vs-none.html) - نوشتهٔ Scott O'Hara
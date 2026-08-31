---
title: "ARIA: aria-label attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-label attribute"
short-title: aria-label
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-label
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-label
sidebar: accessibilitysidebar
---

ویژگی `aria-label` یک مقدار رشته‌ای تعریف می‌کند که می‌تواند برای نام‌گذاری یک عنصر استفاده شود، تا زمانی که نقش عنصر [نام‌گذاری را ممنوع](#associated_roles) نکند.

## توضیحات

گاهی اوقات، {{Glossary("accessible_name", "accessible name")}} پیش‌فرض یک عنصر وجود ندارد یا نام دسترس‌پذیر محتویات عنصر را به‌طور دقیق توصیف نمی‌کند، و محتوای قابل مشاهده‌ای در DOM وجود ندارد که بتوان با شیء مرتبط کرد تا به آن معنا بدهد. یک مثال رایج از چنین عنصری، دکمه‌ای است که حاوی یک آیکون SVG بدون هیچ متنی است.

در مواردی که عنصری که بخشی از [فهرست ممنوع](#associated_roles) نیست، نام دسترس‌پذیری ندارد یا نام دسترس‌پذیر دقیق نیست و محتوای قابل مشاهده‌ای در DOM وجود ندارد که بتوان از طریق ویژگی [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) به آن ارجاع داد، می‌توان از ویژگی `aria-label` برای تعریف رشته‌ای استفاده کرد که عنصر تعاملی مورد نظر را برچسب‌گذاری می‌کند. این کار برای عنصر یک نام دسترس‌پذیر فراهم می‌کند.

کد زیر نمونه‌ای از نحوه استفاده از ویژگی `aria-label` برای ارائه نام دسترس‌پذیر برای یک عنصر `<button>` را نشان می‌دهد. دکمه در این مثال حاوی یک گرافیک SVG است و محتوای متنی ندارد؛ این امر `aria-label` را برای کاربران صفحه‌خوان ضروری می‌کند تا عملکرد آن را درک کنند، که در این مورد «Close» است.

```html
<button aria-label="Close">
  <svg
    aria-hidden="true"
    focusable="false"
    width="17"
    height="17"
    xmlns="http://www.w3.org/2000/svg">
    <path
      d="m.967 14.217 5.8-5.906-5.765-5.89L3.094.26l5.783 5.888L14.66.26l2.092 2.162-5.766 5.889 5.801 5.906-2.092 2.162-5.818-5.924-5.818 5.924-2.092-2.162Z"
      fill="black" />
  </svg>
</button>
```

```js
document.querySelector("button").addEventListener("click", () => {
  myDialog.close();
});
```

> [!NOTE]
> `aria-label` برای نام‌گذاری عناصری در نظر گرفته شده است که نقش ضمنی یا صریح آن‌ها نام‌گذاری را ممنوع نمی‌کند. به‌شدت توصیه می‌شود که اگر برچسب قابل مشاهده‌ای برای عنصر وجود دارد، استفاده از `aria-labelledby` بر `aria-label` اولویت داشته باشد تا عنصر بتواند از آن ارجاع گرفته و نام خود را دریافت کند.

بیشتر محتوا دارای نام دسترس‌پذیری است که از محتوای متنی عنصر بلافاصله احاطه‌کنندهٔ آن تولید می‌شود. نام‌های دسترس‌پذیر همچنین می‌توانند توسط ویژگی‌ها یا عناصر مرتبط ایجاد شوند.

به‌طور پیش‌فرض، نام دسترس‌پذیر یک دکمه محتوای بین تگ‌های باز و بسته {{HTMLElement('button')}} است، نام دسترس‌پذیر یک تصویر محتوای ویژگی [`alt`](/en-US/docs/Web/HTML/Reference/Elements/img#alt) آن است، و نام دسترس‌پذیر یک ورودی فرم محتوای عنصر مرتبط {{HTMLElement('label')}} است.

اگر هیچ‌یک از این گزینه‌ها در دسترس نیست یا اگر نام دسترس‌پذیر پیش‌فرض مناسب نیست، از ویژگی `aria-label` برای تعریف نام دسترس‌پذیر یک عنصر استفاده کنید.

> [!NOTE]
> در حالی که `aria-label` می‌تواند بر روی هر عنصری که می‌تواند نام دسترس‌پذیر داشته باشد استفاده شود، با این حال در عمل فقط بر روی عناصر تعاملی، [ابزارک‌ها](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles#2._widget_roles)، [نقطه‌های عطف](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles#3._landmark_roles)، تصاویر و iframe ها پشتیبانی می‌شود.

هنگام استفاده از `aria-label`، باید [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) را نیز در نظر بگیرید:

- می‌توان از `aria-label` در مواردی استفاده کرد که متنی که می‌تواند عنصر را برچسب‌گذاری کند _قابل مشاهده نیست_. اگر متن قابل مشاهده‌ای وجود دارد که عنصر را برچسب‌گذاری می‌کند، به جای آن از `aria-labelledby` استفاده کنید.
- هدف `aria-label` همان هدف `aria-labelledby` است. هر دو یک نام دسترس‌پذیر برای یک عنصر فراهم می‌کنند. اگر نام قابل مشاهده‌ای برای عنصری که می‌توانید ارجاع دهید وجود ندارد، از `aria-label` برای ارائه نام دسترس‌پذیر قابل تشخیص به کاربر استفاده کنید. اگر متن برچسب در DOM موجود است و امکان ارجاع به آن برای تجربه کاربری قابل قبول وجود دارد، ترجیح دهید از `aria-labelledby` استفاده کنید. از هر دو روی یک عنصر استفاده نکنید، زیرا اگر هر دو اعمال شوند، `aria-labelledby` بر `aria-label` اولویت خواهد داشت.

هنگام استفاده از `aria-label`، نکات اضافی زیر را در نظر داشته باشید:

- ویژگی `aria-label` می‌تواند با عناصر HTML معمولی و معنایی استفاده شود؛ محدود به عناصری نیست که یک [نقش ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles) به آن‌ها اختصاص یافته باشد.
- از `aria-label` «بیش‌ازحد استفاده» نکنید. به یاد داشته باشید که این ویژگی در درجه اول برای فناوری‌های کمکی است. برای ارائه دستورالعمل‌های اضافی یا شفاف‌سازی رابط کاربری، از متن قابل مشاهده با `aria-describedby` یا [`aria-description`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-description) استفاده کنید، نه `aria-label`. دستورالعمل‌ها باید برای همه کاربران قابل دسترس باشند، نه فقط برای کسانی که از صفحه‌خوان استفاده می‌کنند (یا ترجیحاً رابط کاربری خود را شهودی‌تر کنید).

  > [!NOTE]
  > از آنجا که محتوای `aria-label` در خارج از فناوری‌های کمکی نمایش داده نمی‌شود، در نظر داشته باشید اطلاعات مهم برای همه کاربران قابل مشاهده باشد.

- همه عناصر نمی‌توانند نام دسترس‌پذیر داشته باشند. نه `aria-label` و نه `aria-labelledby` نباید با نقش‌های ساختاری درون‌خطی مانند `code`، `term` و `emphasis`، و نقش‌هایی که به API دسترس‌پذیری نگاشت نشده‌اند، از جمله `none` استفاده شوند. ویژگی `aria-label` برای عناصری از جمله پیوندها، ویدیوها، کنتزل‌های فرم و عناصری با [نقش‌های نقطه عطف](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles#3._landmark_roles) یا [نقش‌های ابزارک](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles#2._widget_roles) در نظر گرفته شده است؛ `aria-label` زمانی نام دسترس‌پذیر فراهم می‌کند که هیچ برچسب قابل مشاهده‌ای در DOM وجود نداشته باشد.
- اگر یک `title` به یک {{HTMLElement('iframe')}} اختصاص دهید، یک ویژگی `alt` برای یک {{HTMLElement('img')}} تعریف کنید، یا یک {{HTMLElement('label')}} برای یک {{HTMLElement('input')}} اضافه کنید، `aria-label` لازم نیست. با این حال، اگر ویژگی `aria-label` وجود داشته باشد، بر `title` iframe، `alt` تصویر یا متن `<label>` ورودی به عنوان نام دسترس‌پذیر آن عنصر اولویت خواهد داشت.

## مقادیر

- `<string>`
  - : یک رشته متنی که نام دسترس‌پذیر برای شیء خواهد بود.

## رابط‌های مرتبط

- {{domxref("Element.ariaLabel")}}
  - : ویژگی [`ariaLabel`](/en-US/docs/Web/API/Element/ariaLabel)، بخشی از رابط {{domxref("Element")}}، مقدار ویژگی `aria-label` را منعکس می‌کند.
- {{domxref("ElementInternals.ariaLabel")}}
  - : ویژگی [`ariaLabel`](/en-US/docs/Web/API/ElementInternals/ariaLabel)، بخشی از رابط {{domxref("ElementInternals")}}، مقدار ویژگی `aria-label` را منعکس می‌کند.

## نقش‌های مرتبط

در تقریباً همه نقش‌ها استفاده می‌شود **به‌جز** نقش‌هایی که نمی‌توان توسط نویسنده نام دسترس‌پذیری برای آن‌ها فراهم کرد.

ویژگی `aria-label` در موارد زیر **پشتیبانی نمی‌شود**:

- [`caption`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)
- [`code`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)
- [`definition`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)
- [`deletion`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)
- [`emphasis`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)
- [`generic`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/generic_role)
- [`insertion`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)
- [`mark`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/mark_role)
- [`paragraph`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)
- [`presentation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role) / [`none`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/none_role)
- [`strong`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)
- [`subscript`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)
- [`suggestion`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/suggestion_role)
- [`superscript`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)
- [`term`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/term_role)
- [`time`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)

## مشخصات

{{Specifications}}

## همچنین ببینید

- عنصر {{HTMLElement('label')}}
- [`aria-description`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-description)
- [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby)
- [استفاده از نقش‌های نقطه عطف HTML برای بهبود دسترس‌پذیری](/en-US/blog/aria-accessibility-html-landmark-roles/) در وبلاگ MDN (2023)
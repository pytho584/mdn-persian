---
title: "ARIA: aria-details attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-details"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-details attribute"
short-title: aria-details
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-details
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-details
sidebar: accessibilitysidebar
---

ویژگی سراسری `aria-details` عنصر (یا عناصری) را شناسایی می‌کند که اطلاعات اضافی مرتبط با شیء را فراهم می‌کنند.

## توضیحات

ویژگی `aria-details` می‌تواند برای ارائه اطلاعات تکمیلی یا توضیحات پیچیده به یک شیء استفاده شود. این ویژگی برای آگاه‌سازی کاربران فناوری‌های کمکی درباره محتوا با فراهم کردن اطلاعات عمیق‌تر استفاده می‌شود، خواه آن محتوا در سند فعلی باشد یا پیوندی به منابع اضافی.

خواص HTML و WAI-ARIA دیگری نیز وجود دارند که اهداف مشابهی دارند. عنصر HTML {{HTMLElement('label')}} و خواص [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) و [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) برای ارائه برچسب‌های کوتاه برای یک شیء استفاده می‌شوند. ویژگی `title` در HTML و خواص [`aria-description`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-description) و [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby) توضیحات متنی طولانی‌تری برای یک شیء فراهم می‌کنند. با این حال، هنگامی که اطلاعات اضافی، توضیحات پیچیده، یا محتوای قابل پیمایش مرتبط با شیء ضروری و در دسترس است، باید از ویژگی `aria-details` استفاده شود.

ویژگی `aria-details` هدفی مشابه با ویژگی `longdesc` در HTML دارد — که هرگز به طور کامل پشتیبانی نشد — یعنی URL یک توضیح طولانی برای محتوای یک عنصر جایگزین‌شده — که به دلیل عدم پشتیبانی و استفاده نادرست منسوخ شد.

ویژگی `aria-details` مقدار [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) یا فهرستی از `id`ها که با فاصله جدا شده‌اند را به عنوان مقدار خود می‌پذیرد تا اطلاعات دقیق‌تری از عناصر به دست آورد. هنگامی که `aria-details` روی یک عنصر قرار می‌گیرد، فناوری‌های کمکی کاربران را از وجود اطلاعات توسعه‌یافته آگاه می‌کنند و به کاربر امکان می‌دهند به محتوای ارجاع‌داده‌شده برود.

عناصری که توسط `aria-details` ارجاع داده می‌شوند، برای حاوی اطلاعات بیشتری نسبت به آنچه معمولاً از طریق [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby) ارائه می‌شود، در نظر گرفته شده‌اند.

عناصر ارجاع‌داده‌شده توسط `aria-details` باید برای همه کاربران قابل مشاهده باشند. `aria-details` به کاربرانی اطلاع می‌دهد که ممکن است نتوانند صفحه را اسکن کنند و به سرعت تشخیص دهند که محتوای توضیحی در دسترس است.

> [!NOTE]
> `aria-details` تأثیری بر توصیف قابل دسترس ندارد.

برخلاف `aria-describedby`، عناصری که توسط `aria-details` ارجاع داده می‌شوند در توصیف‌های قابل دسترس استفاده نمی‌شوند و هنگام ارائه به کاربران فناوری کمکی به یک رشته ساده تبدیل نمی‌شوند. اگر محتوای مرتبط خیلی طولانی نیست و تبدیل محتویات عنصر ارجاع‌داده‌شده به یک رشته ساده متنی باعث از دست رفتن اطلاعات نمی‌شود، به جای آن از `aria-describedby` استفاده کنید. با این وجود، معتبر است که یک عنصر هم `aria-details` و هم یک توصیف مشخص‌شده با `aria-describedby` یا `aria-description` داشته باشد.

## مثال

در مورد نقش‌های «تعریف» و «اصطلاح»، `aria-details` روی عنصر [`term`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/term_role) با `id` عنصری که نقش [`definition`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/definition_role) را دارد، قرار می‌گیرد.

```html
<p>
  The <strong>cubic-bezier()</strong> functional notation defines a cubic
  <span role="term" aria-details="bezier bezImg">Bézier curve</span>. As these
  curves are continuous, they are often used to smooth down the start and end of
  the curve and are therefore sometimes called easing functions.
</p>

<p role="definition" id="bezier">
  A <strong>Bézier curve</strong>, (Pronounced \ ˈbe-zē-ˌā \)
  <i aria-description="English pronunciation">BEH-zee-ay</i>) is a
  mathematically described curve used in computer graphics and animation. The
  curve is defined by a set of control points with a minimum of two. Web related
  graphics and animations use Cubic Béziers, which are curves with four control
  points P<sub>0</sub>, P<sub>1</sub>, P<sub>2</sub>, and P<sub>3</sub>.
</p>

<a
  href="bezierExplanation.html"
  id="bezImg"
  aria-label="Explanation of Bézier curve in CSS easing functions">
  <img alt="Animated Bézier curve showing 4 control points." src="bezier.gif" />
</a>
```

## مقادیر

- فهرست مرجع شناسه (ID reference list)
  - : یک `id` یا فهرستی از `id`ها که با فاصله جدا شده‌اند از عناصری که اطلاعات اضافی مرتبط را فراهم می‌کنند یا به آن‌ها پیوند می‌دهند.

## رابط‌های مرتبط

- {{domxref("Element.ariaDetailsElements")}}
  - : ویژگی `ariaDetailsElements` بخشی از رابط هر عنصر است.
    مقدار آن آرایه‌ای از زیرکلاس‌های {{domxref("Element")}} است که ارجاع‌های `id` در ویژگی `aria-details` را منعکس می‌کنند ([با برخی ملاحظات](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references)).
- {{domxref("ElementInternals.ariaDetailsElements")}}
  - : ویژگی `ariaDetailsElements` بخشی از رابط هر عنصر سفارشی است.
    مقدار آن آرایه‌ای از زیرکلاس‌های {{domxref("Element")}} است که ارجاع‌های `id` در ویژگی `aria-details` را منعکس می‌کنند ([با برخی ملاحظات](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references)).

## نقش‌های مرتبط

در **همه** نقش‌ها استفاده می‌شود.

## مشخصات

{{Specifications}}

## همچنین ببینید

- ویژگی HTML [id](/en-US/docs/Web/HTML/Reference/Global_attributes/id)
- [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby)
- [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby)
- [`aria-description`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-description)
- [ویژگی `alt` تصویر](/en-US/docs/Web/API/HTMLImageElement/alt)
- ویژگی HTML [title](/en-US/docs/Web/HTML/Reference/Global_attributes/title)
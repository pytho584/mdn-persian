---
title: "ARIA: aria-hidden attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-hidden"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-hidden attribute"
short-title: aria-hidden
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-hidden
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-hidden
sidebar: accessibilitysidebar
---

# ARIA: ویژگی aria-hidden

وضعیت `aria-hidden` نشان می‌دهد که آیا عنصر در معرض یک API دسترس‌پذیری قرار می‌گیرد یا خیر.

## توضیحات

از ویژگی `aria-hidden` می‌توان برای پنهان کردن محتوای غیرتعاملی از API دسترس‌پذیری استفاده کرد.

افزودن `aria-hidden="true"` به یک عنصر، آن عنصر و همه فرزندانش را از درخت دسترس‌پذیری حذف می‌کند. این کار می‌تواند تجربه کاربران فناوری کمکی را با پنهان کردن موارد زیر بهبود بخشد:

- محتوای صرفاً تزئینی، مانند آیکون‌ها یا تصاویر
- محتوای تکراری، مانند متن تکرارشده
- محتوای خارج از صفحه یا جمع‌شده، مانند منوها

وجود ویژگی `aria-hidden` محتوا را از فناوری کمکی پنهان می‌کند، اما از نظر بصری چیزی را پنهان نمی‌کند.

`aria-hidden="true"` نباید روی عناصری که می‌توانند فوکوس دریافت کنند استفاده شود. علاوه بر این، چون این ویژگی توسط فرزندان یک عنصر به ارث برده می‌شود، نباید به والد یا اجداد یک عنصر قابل فوکوس اضافه شود.

> [!WARNING]
> از `aria-hidden="true"` روی عناصر قابل فوکوس استفاده نکنید.

> [!NOTE]
> هنگام پنهان کردن محتوای قابل مشاهده از فناوری‌های کمکی، همه ناتوانی‌ها را در نظر بگیرید. همه کاربران فناوری کمکی کم‌بینا نیستند. اگر محتوای قابل مشاهده با محتوای متنی در API دسترس‌پذیری مطابقت نداشته باشد، تجربه کاربری برای کاربران بینا تحت تأثیر منفی قرار می‌گیرد.

در ظاهر، `aria-hidden="true"` و `role="presentation"` و مترادف آن `role="none"` مشابه به نظر می‌رسند، اما هدف پشت هر یک متفاوت است.

- `aria-hidden="true"` کل عنصر را از API دسترس‌پذیری حذف می‌کند.
- `role="presentation"` و `role="none"` معنای معنایی یک عنصر را حذف می‌کنند، در حالی که همچنان آن عنصر و محتوایش را در معرض فناوری کمکی قرار می‌دهند.

`aria-hidden="true"` نباید در موارد زیر اضافه شود:

- ویژگی [`hidden`](/en-US/docs/Web/HTML/Reference/Global_attributes/hidden) در HTML وجود داشته باشد
- عنصر یا جد عنصر با [`display: none`](/en-US/docs/Web/CSS/Reference/Properties/display) پنهان شده باشد
- عنصر یا جد عنصر با [`visibility: hidden`](/en-US/docs/Web/CSS/Reference/Properties/visibility) پنهان شده باشد

در هر سه سناریو، افزودن این ویژگی ضروری نیست، زیرا عنصر قبلاً از درخت دسترس‌پذیری حذف شده است. پنهان کردن بصری عناصر با `display` یا `visibility` محتوا را از صفحه نمایش و از فناوری‌های کمکی پنهان می‌کند.

استفاده از `aria-hidden="false"` اگر هر یک از والدین آن `aria-hidden="true"` را مشخص کرده باشند، عنصر را دوباره در معرض فناوری کمکی قرار نمی‌دهد.

## مثال

افزودن `aria-hidden="true"` به آیکون، کاراکتر آیکون را از قرار گرفتن در نام قابل دسترس پنهان می‌کند.

```html
<button>
  <span class="fa fa-tweet" aria-hidden="true"></span>
  <span class="label"> Tweet </span>
</button>
```

ما یک دکمه با [آیکون Font Awesome](https://fontawesome.com/) داریم. آیکون را با `aria-hidden="true"` از فناوری‌های کمکی پنهان می‌کنیم، زیرا قرار دادن آیکون در معرض فناوری‌های کمکی می‌تواند منجر به افزونگی یا، اگر آیکون محتوای یکسانی با متن قابل مشاهده نداشته باشد، سردرگمی شود.

## مقادیر

- `false`
  - : عنصر به‌گونه‌ای در معرض API دسترس‌پذیری قرار می‌گیرد که گویی رندر شده است.
- `true`
  - : عنصر از API دسترس‌پذیری پنهان است.
- `undefined` (پیش‌فرض)
  - : وضعیت پنهان عنصر توسط عامل کاربر بر اساس اینکه آیا رندر شده است تعیین می‌شود.

## رابط‌های مرتبط

- {{domxref("Element.ariaHidden")}}
  - : ویژگی [`ariaHidden`](/en-US/docs/Web/API/Element/ariaHidden)، بخشی از رابط {{domxref("Element")}}، مقدار ویژگی `aria-hidden` را منعکس می‌کند که نشان می‌دهد آیا عنصر در معرض API دسترس‌پذیری قرار می‌گیرد یا خیر.
- {{domxref("ElementInternals.ariaHidden")}}
  - : ویژگی [`ariaHidden`](/en-US/docs/Web/API/ElementInternals/ariaHidden)، بخشی از رابط {{domxref("ElementInternals")}}، مقدار ویژگی `aria-hidden` را منعکس می‌کند.

## نقش‌های مرتبط

مورد استفاده در **همه** نقش‌ها

## مشخصات

{{Specifications}}

## همچنین ببینید

- [`aria-disabled`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-disabled)
- [`aria-modal`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-modal)
- [`aria-expanded`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-expanded)
- ویژگی HTML [`hidden`](/en-US/docs/Web/HTML/Reference/Global_attributes/hidden)
- ویژگی CSS {{CSSXref('display')}}
- ویژگی CSS {{CSSXref('visibility')}}
---
title: "ARIA: aria-valuenow attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuenow"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-valuenow attribute"
short-title: aria-valuenow
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-valuenow
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-valuenow
sidebar: accessibilitysidebar
---

ویژگی `aria-valuenow` مقدار فعلی را برای یک ویجت `range` تعریف می‌کند.

## توضیحات

ویژگی `aria-valuenow` مقدار فعلی را برای ویجت‌های range تعریف می‌کند. این ویژگی مشابه ویژگی `value` در {{HTMLElement('progress')}}، {{HTMLElement('meter')}} و {{HTMLElement('input')}} از نوع [`range`](/en-US/docs/Web/HTML/Reference/Elements/input/range)، [`number`](/en-US/docs/Web/HTML/Reference/Elements/input/number) و همه انواع تاریخ-زمان است.

هنگام ایجاد نقشی از نوع range، شامل [`meter`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/meter_role)، [`scrollbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/scrollbar_role)، [`slider`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/slider_role) و [`spinbutton`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/spinbutton_role) روی یک عنصر غیرمعنایی، `aria-valuenow` امکان تعریف یک مقدار عددی فعلی بین مقادیر حداقل و حداکثر را می‌دهد. مقادیر حداقل و حداکثر با [`aria-valuemin`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemin) و [`aria-valuemax`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemax) تعریف می‌شوند.

> [!WARNING]
> نقش [`range`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/range_role) به خودی خود **نباید** استفاده شود، زیرا یک نقش [«abstract»](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles#6._abstract_roles) است. ویژگی `aria-valuenow` بر روی همه زیرنوع‌های نقش‌های range استفاده می‌شود.

```html
<p id="birthyearLabel">What year were you born?</p>
<div
  role="spinbutton"
  tabindex="-1"
  aria-valuenow="1984"
  aria-valuemin="1900"
  aria-valuemax="2021"
  aria-labelledby="birthyearLabel">
  <span class="value"> 1984 </span>
  <span role="button">
    <span aria-hidden="true">+</span>
    Increment year by 1
  </span>
  <span role="button">
    <span aria-hidden="true">-</span>
    Decrement year by 1
  </span>
</div>
```

در صورت امکان از عناصر HTML معنایی استفاده کنید:

```html
<label for="birthyear">What year were you born?</label>
<input type="number" id="birthyear" value="1984" min="1900" max="2021" />
```

اگر مقدار مشخصی وجود ندارد، مانند زمانی که یک نوار پیشرفت در وضعیت نامعین است، ویژگی `aria-valuenow` را تنظیم نکنید.

وقتی `aria-valuenow` تنظیم نشده باشد، هیچ اطلاعاتی درباره مقدار فعلی در نظر گرفته نمی‌شود.

هنگام استفاده با اسلایدرها و spinbuttonها، فناوری‌های کمکی مقدار واقعی را به کاربران اعلام می‌کنند.

هنگام استفاده با progressbar و scrollbar، فناوری‌های کمکی مقدار را به‌صورت درصد به کاربران اعلام می‌کنند. وقتی هر دو `aria-valuemin` و `aria-valuemax` تعریف شده باشند، مقدار درصد به‌عنوان موقعیتی در محدوده محاسبه می‌شود. در غیر این صورت، مقدار واقعی به‌صورت درصد اعلام می‌شود.

وقتی مقداری که باید اعلام شود، خواه مقدار واقعی یا مقدار به‌صورت درصد، ممکن است برای کاربران واضح نباشد، باید از ویژگی [`aria-valuetext`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuetext) برای ارائه نمایشی کاربرپسند از مقدار استفاده شود. وقتی تنظیم شد، رشته valuetext به جای مقدار عددی valuenow اعلام می‌شود. برای مثال، اگر یک اسلایدر روزهای هفته را نشان دهد، به‌طوری‌که `aria-valuenow` روز هفته یک عدد است، ویژگی `aria-valuetext` باید روی رشته‌ای تنظیم شود که مقدار اسلایدر را قابل فهم کند، مانند «دوشنبه».

## مثال‌ها

```html
<p id="temperatureLabel">Oven Temperature</p>
<div
  role="meter"
  id="temperature"
  aria-valuenow="205"
  aria-valuemin="70"
  aria-valuemax="250"
  aria-labelledby="temperatureLabel">
  <div class="meter-color" aria-hidden="true"></div>
</div>
```

اولین قانون استفاده از ARIA این است: «اگر می‌توانید از یک ویژگی بومی با معناشناسی و رفتاری که از قبل به آن نیاز دارید استفاده کنید، به جای تغییر کاربری یک عنصر و **افزودن** نقش، حالت یا ویژگی ARIA برای قابل دسترس ساختن آن، این کار را انجام دهید.»

```html
<label for="temperature">Oven Temperature</label>
<input type="range" id="temperature" value="205" min="70" max="250" step="5" />
```

اگر از معناشناسی بومی HTML با {{HTMLElement('input')}} استفاده کنیم، استایل‌ها و معناشناسی را به رایگان به دست می‌آوریم.

## مقادیر

- `<number>`
  - : یک عدد اعشاری، بین مقادیر حداقل و حداکثر.

## رابط‌های مرتبط

- {{domxref("Element.ariaValueNow")}}
  - : ویژگی [`ariaValueNow`](/en-US/docs/Web/API/Element/ariaValueNow) که بخشی از رابط {{domxref("Element")}} است، مقدار ویژگی `aria-valuenow` را منعکس می‌کند.
- {{domxref("ElementInternals.ariaValueNow")}}
  - : ویژگی [`ariaValueNow`](/en-US/docs/Web/API/ElementInternals/ariaValueNow) که بخشی از رابط {{domxref("ElementInternals")}} است، مقدار ویژگی `aria-valuenow` را منعکس می‌کند.

## نقش‌های مرتبط

استفاده‌شده در نقش‌ها:

- [`meter`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/meter_role)
- [`scrollbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/scrollbar_role)
- [`separator`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/separator_role)
- [`slider`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/slider_role)
- [`spinbutton`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/spinbutton_role)

به ارث برده‌شده در نقش‌ها:

- [`meter`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/meter_role)
- [`progressbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/progressbar_role)
- [`scrollbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/scrollbar_role)
- [`slider`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/slider_role)
- [`spinbutton`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/spinbutton_role)

## مشخصات

{{Specifications}}

## همچنین ببینید

- [نقش `range`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/range_role)
- [ویژگی `value` عنصر `<input type="range>`](/en-US/docs/Web/HTML/Reference/Elements/input/range#value)
- [`aria-valuetext`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuetext)
- [`aria-valuemax`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemax)
- [`aria-valuemin`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemin)
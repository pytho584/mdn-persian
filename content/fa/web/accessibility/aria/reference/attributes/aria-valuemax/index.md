---
title: "ARIA: aria-valuemax attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemax"
translated_by: "n8n + AI"
short-title: aria-valuemax
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-valuemax
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-valuemax
sidebar: accessibilitysidebar
---

ویژگی `aria-valuemax` حداکثر مقدار مجاز را برای یک ویجت محدوده تعریف می‌کند.

## توضیحات

ویژگی `aria-valuemax` حداکثر مقدار مجاز را برای ویجت‌های محدوده تعریف می‌کند. این ویژگی مشابه ویژگی `max` عناصر {{HTMLElement('progress')}}، {{HTMLElement('meter')}} و {{HTMLElement('input')}} از نوع [`range`](/en-US/docs/Web/HTML/Reference/Elements/input/range)، [`number`](/en-US/docs/Web/HTML/Reference/Elements/input/number) و تمام انواع تاریخ-زمان است.

هنگام ایجاد یک نقش از نوع محدوده، شامل [`meter`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/meter_role)، [`scrollbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/scrollbar_role)، [`slider`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/slider_role) و [`spinbutton`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/spinbutton_role) روی یک عنصر غیر معنایی، `aria-valuemax` امکان تعریف حداکثر مقداری که بیشتر از حداقل مقدار است را فراهم می‌کند و یک ویژگی ضروری برای `slider`، `scrollbar` و `spinbutton` است.

اعلام حداقل و حداکثر مقادیر به فناوری‌های کمکی امکان می‌دهد تا اندازه محدوده را به کاربران منتقل کنند. حداقل مقدار با [`aria-valuemin`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemin) تعریف می‌شود.

> [!WARNING]
> خود نقش [`range`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/range_role) **نباید** استفاده شود زیرا یک نقش [«انتزاعی»](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles#6._abstract_roles) است. ویژگی `aria-valuemax` در تمام زیرنوع‌های نقش‌های محدوده استفاده می‌شود.

## مثال

کد زیر یک نوار لغزنده با حداکثر مقدار ۹ را نشان می‌دهد.

```html
<div id="dimesLabel">Dimes</div>
<div
  role="slider"
  aria-valuenow="0"
  aria-valuemin="0"
  aria-valuemax="9"
  aria-labelledby="dimesLabel"
  id="dimes"></div>
```

## مقادیر

- `<number>`
  - : یک عدد صحیح یا اعشاری که بزرگتر از حداقل مقدار است.

## رابط‌های مرتبط

- {{domxref("Element.ariaValueMax")}}
  - : ویژگی [`ariaValueMax`](/en-US/docs/Web/API/Element/ariaValueMax) که بخشی از رابط {{domxref("Element")}} است، مقدار ویژگی `aria-valuemax` را منعکس می‌کند.
- {{domxref("ElementInternals.ariaValueMax")}}
  - : ویژگی [`ariaValueMax`](/en-US/docs/Web/API/ElementInternals/ariaValueMax) که بخشی از رابط {{domxref("ElementInternals")}} است، مقدار ویژگی `aria-valuemax` را منعکس می‌کند.

## نقش‌های مرتبط

استفاده شده در نقش‌ها:

- [`meter`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/meter_role)
- [`scrollbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/scrollbar_role) (ضروری)
- [`separator`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/separator_role)
- [`slider`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/slider_role) (ضروری)
- [`spinbutton`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/spinbutton_role) (ضروری)

به ارث رسیده به نقش‌ها:

- [`meter`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/meter_role)
- [`progressbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/progressbar_role)
- [`scrollbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/scrollbar_role)
- [`slider`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/slider_role)
- [`spinbutton`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/spinbutton_role)

## مشخصات

{{Specifications}}

## همچنین ببینید

- [`range` نقش](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/range_role)
- [`<input type="range">` عنصر `max` ویژگی](/en-US/docs/Web/HTML/Reference/Elements/input/range#max)
- [`aria-valuemin`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemin)
- [`aria-valuenow`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuenow)
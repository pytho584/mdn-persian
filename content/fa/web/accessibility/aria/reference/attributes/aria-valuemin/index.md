---
title: "ARIA: aria-valuemin attribute"
short-title: aria-valuemin
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-valuemin
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-valuemin
sidebar: accessibilitysidebar
---

ویژگی `aria-valuemin` حداقل مقدار مجاز را برای یک ویجت محدوده تعریف می‌کند.

این ویژگی مشابه ویژگی `min` در عناصر {{HTMLElement('progress')}}، {{HTMLElement('meter')}} و {{HTMLElement('input')}} از نوع [`range`](/en-US/docs/Web/HTML/Reference/Elements/input/range)، [`number`](/en-US/docs/Web/HTML/Reference/Elements/input/number) و تمام انواع تاریخ-زمان است.

هنگام ایجاد یک نقش از نوع محدوده، از جمله [`meter`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/meter_role)، [`scrollbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/scrollbar_role)، [`slider`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/slider_role) و [`spinbutton`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/spinbutton_role) روی یک عنصر غیرمعنایی، `aria-valuemin` امکان تعریف حداقلی کمتر از حداکثر مقدار را فراهم می‌کند و یک ویژگی ضروری برای `slider`، `scrollbar` و `spinbutton` است.

اعلان حداقل و حداکثر مقادیر به فناوری‌های کمکی اجازه می‌دهد تا اندازه محدوده را به کاربران منتقل کنند.

حداکثر مقدار با [`aria-valuemax`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemax) تعریف می‌شود.

> [!WARNING]
> خود نقش [`range`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/range_role) **نباید** استفاده شود زیرا یک [نقش «انتزاعی»](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles#6._abstract_roles) است. ویژگی `aria-valuemin` روی همه زیرنوع‌های نقش محدوده استفاده می‌شود.

## مقادیر

- `<number>`
  - : یک عدد اعشاری، پایین‌تر از حداکثر مقدار.

## رابط‌های مرتبط

- {{domxref("Element.ariaValueMin")}}
  - : ویژگی [`ariaValueMin`](/en-US/docs/Web/API/Element/ariaValueMin) که بخشی از رابط {{domxref("Element")}} است، مقدار ویژگی `aria-valuemin` را منعکس می‌کند.
- {{domxref("ElementInternals.ariaValueMin")}}
  - : ویژگی [`ariaValueMin`](/en-US/docs/Web/API/ElementInternals/ariaValueMin) که بخشی از رابط {{domxref("ElementInternals")}} است، مقدار ویژگی `aria-valuemin` را منعکس می‌کند.

## نقش‌های مرتبط

مورد استفاده در نقش‌ها:

- [`meter`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/meter_role)
- [`scrollbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/scrollbar_role)
- [`separator`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/separator_role)
- [`slider`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/slider_role)
- [`spinbutton`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/spinbutton_role)

به ارث رفته در نقش‌ها:

- [`meter`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/meter_role)
- [`progressbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/progressbar_role)
- [`scrollbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/scrollbar_role)
- [`slider`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/slider_role)
- [`spinbutton`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/spinbutton_role)

## مشخصات

{{Specifications}}

## همچنین ببینید

- [نقش `range`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/range_role)
- [ویژگی `min` عنصر `<input type="range">`](/en-US/docs/Web/HTML/Reference/Elements/input/range#min)
- [`aria-valuemax`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemax)
- [`aria-valuenow`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuenow)
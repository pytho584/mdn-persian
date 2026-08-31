---
title: "ARIA: aria-valuetext attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuetext"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-valuetext attribute"
short-title: aria-valuetext
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-valuetext
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-valuetext
sidebar: accessibilitysidebar
---

ویژگی `aria-valuetext` جایگزین متنی قابل‌فهم برای انسان از `aria-valuenow` را در یک ابزارک بازه تعریف می‌کند.

## توضیحات

اعداد — حتی درصدها — همیشه کاربرپسند نیستند. فناوری‌های کمکی [`aria-valuenow`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuenow) را به‌عنوان مقادیر عددی ارائه می‌دهند. اگر نوار پیشرفت روی ۸٪ باشد، این یعنی چه؟ `aria-valuetext` روشی برای ارائه مقدار فعلی به‌صورت کاربرپسندتر و قابل‌فهم‌تر برای انسان فراهم می‌کند. برای مثال، مقدار یک نشانگر باتری می‌تواند به‌صورت `aria-valuetext="8% (34 minutes) remaining"` بیان شود.

ویژگی `aria-valuetext` همراه با ویژگی `aria-valuenow` استفاده می‌شود، نه به‌جای آن، مگر اینکه مقدار نامعلوم باشد.

`aria-valuetext` تنها زمانی لازم است که مقدار عددی `aria-valuenow` معنادار نباشد. برای مثال، مقادیر یک محدوده عددی هستند اما ممکن است برای مقادیر غیرعددی مانند سطح کلاس دانشگاه استفاده شوند. مقادیر `aria-valuenow` برای یک دانشگاه چهارساله می‌تواند از ۱ تا ۴ باشد که موقعیت هر مقدار را در فضای مقدار نشان می‌دهد. در این حالت، `aria-valuetext` می‌تواند یکی از رشته‌ها باشد: «سال اول»، «سال دوم»، «سال سوم» و «سال چهارم».

اگر مقدار عددی معنادار باشد، مانند یک spinner با `aria-valuenow="3"` برای تعداد تکه‌های پیتزایی که می‌خواهید سفارش دهید، `aria-valuetext` مورد نیاز نیست.

وقتی هر دو `aria-valuetext` و `aria-valuenow` وجود داشته باشند، `aria-valuetext` اعلام می‌شود. وقتی ویژگی `aria-valuetext` وجود نداشته باشد، فناوری‌های کمکی ویژگی `aria-valuenow` را برای مقدار فعلی اعلام می‌کنند.

## مقادیر

- `<string>`
  - : یک جایگزین متنی قابل‌فهم برای انسان از مقدار `aria-valuenow`.

## رابط‌های مرتبط

- {{domxref("Element.ariaValueText")}}
  - : ویژگی [`ariaValueText`](/en-US/docs/Web/API/Element/ariaValueText) که بخشی از رابط {{domxref("Element")}} است، مقدار ویژگی `aria-valuetext` را بازتاب می‌دهد.
- {{domxref("ElementInternals.ariaValueText")}}
  - : ویژگی [`ariaValueText`](/en-US/docs/Web/API/ElementInternals/ariaValueText) که بخشی از رابط {{domxref("ElementInternals")}} است، مقدار ویژگی `aria-valuetext` را بازتاب می‌دهد.

## نقش‌های مرتبط

استفاده در نقش‌ها:

- [`range`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/range_role)
- [`separator`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/separator_role)
- [`spinbutton`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/spinbutton_role)

به‌ارث‌رفته در نقش‌ها:

- [`meter`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/meter_role)
- [`progressbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/progressbar_role)
- [`scrollbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/scrollbar_role)
- [`slider`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/slider_role)
- [`spinbutton`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/spinbutton_role)

## مشخصات

{{Specifications}}

## جستارهای وابسته

- [`aria-valuenow`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuenow)
---
title: "ARIA: aria-pressed attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-pressed"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-pressed attribute"
short-title: aria-pressed
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-pressed
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-pressed
sidebar: accessibilitysidebar
---

ویژگی `aria-pressed` وضعیت فعلی «فشرده‌شده» یک دکمهٔ تغییر وضعیت را نشان می‌دهد.

## توضیحات

افزودن `aria-pressed` به عنصری با نقش [`button`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/button_role) آن را به یک دکمهٔ تغییر وضعیت تبدیل می‌کند. ویژگی `aria-pressed` فقط برای دکمه‌های تغییر وضعیت مرتبط است. این ویژگی وضعیت «فشرده‌شده» فعلی دکمه را نشان می‌دهد.

این ویژگی «سه‌حالته» است، به این معنی که مقدار آن می‌تواند `true`، `false`، `mixed` یا `undefined` باشد. در مورد `aria-pressed`، مانند بسیاری از انواع مقدار سه‌حالته، مقدار پیش‌فرض `undefined` است.

دکمه‌های تغییر وضعیت برای تغییر مقدار خود به یک چرخهٔ کامل فشار دادن و رها کردن نیاز دارند. یک بار فشار دادن و رها کردن آن، مقدار را به `true` تغییر می‌دهد. اگر دوباره فشار داده و رها شود، مقدار به `false` بازمی‌گردد.

مقدار `mixed` یعنی مقادیرِ بیش از یک آیتم که توسط دکمه کنترل می‌شوند، همگی یکسان نیستند.

هنگام تغییر وضعیت، محتوای برچسب روی یک دکمهٔ تغییر وضعیت را تغییر ندهید. اگر برچسب یک دکمه «Pause» است، هنگام فشار دادن آن را به «Play» تغییر ندهید. در این مثال، وقتی وضعیت فشرده‌شده true است، برچسب همچنان «Pause» می‌ماند، بنابراین صفحه‌خوان چیزی مانند «Pause toggle button pressed» را اعلام می‌کند.

```html
<button aria-pressed="false">Pause</button>
```

اگر می‌خواهید برچسب بین «Paused» و «Play» تغییر کند، از `aria-pressed` استفاده نکنید.

اولین قانون استفاده از ARIA این است: «اگر می‌توانید از یک ویژگی بومی با معنا و رفتاری که از قبل در آن تعبیه شده استفاده کنید، به جای تغییر کاربری یک عنصر و افزودن نقش، حالت یا ویژگی ARIA برای قابل دسترس کردن آن، این کار را انجام دهید.» اگر از معنای بومی HTML با {{HTMLElement('button')}} استفاده کنیم، می‌توانیم برچسب را تغییر دهیم به جای تغییر حالت فشرده، و نیازی به ویژگی `aria-pressed` نخواهیم داشت.

## مقادیر

- `false`
  - : دکمه از فشرده‌شدن پشتیبانی می‌کند اما در حال حاضر فشرده نشده است.
- `mixed`
  - : مقدار حالت مختلط را برای یک دکمهٔ تغییر وضعیت سه‌حالته نشان می‌دهد.
- `true`
  - : دکمه فشرده شده است.
- `undefined` (پیش‌فرض)
  - : عنصر از فشرده‌شدن پشتیبانی نمی‌کند.

## رابط‌های مرتبط

- {{domxref("Element.ariaPressed")}}
  - : ویژگی [`ariaPressed`](/en-US/docs/Web/API/Element/ariaPressed) که بخشی از رابط {{domxref("Element")}} است، مقدار ویژگی `aria-pressed` را بازتاب می‌دهد.
- {{domxref("ElementInternals.ariaPressed")}}
  - : ویژگی [`ariaPressed`](/en-US/docs/Web/API/ElementInternals/ariaPressed) که بخشی از رابط {{domxref("ElementInternals")}} است، مقدار ویژگی `aria-pressed` را بازتاب می‌دهد.

## نقش‌های مرتبط

- [`button`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/button_role)

## مشخصات

{{Specifications}}

## جستارهای وابسته

- [`<input type="button">`](/en-US/docs/Web/HTML/Reference/Elements/input/button)
- [`<input type="submit">`](/en-US/docs/Web/HTML/Reference/Elements/input/submit)
- {{HTMLElement('button')}}
- [`aria-checked`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-checked)
- [`aria-selected`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-selected)
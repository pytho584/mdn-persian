---
title: "ARIA: suggestion role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/suggestion_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: suggestion role"
short-title: suggestion
slug: Web/Accessibility/ARIA/Reference/Roles/suggestion_role
page-type: aria-role
sidebar: accessibilitysidebar
---

نقش `suggestion` از نظر معنایی یک تغییر پیشنهادی واحد در یک سند قابل ویرایش را نشان می‌دهد. این نقش باید روی عنصری استفاده شود که یک عنصر با نقش `insertion` و یک عنصر با نقش `deletion` را در بر می‌گیرد.

## مثال‌ها

وقتی تغییری در محتوا دارید که شامل یک درج _و_ یک حذف است، کاربر صفحه‌خوان هیچ راهی برای تشخیص اینکه این دو به هم مرتبط هستند یا نه ندارد. این وظیفهٔ `role="suggestion"` است که باید روی عنصری قرار گیرد که هر دو را در بر می‌گیرد، مانند زیر:

```html
<p>
  Freida's pet is a
  <span role="suggestion">
    <span role="deletion">black Cat called Luna</span>
    <span role="insertion">purple T. Rex called Tiny</span></span
  >.
</p>
```

ما حتی می‌توانیم یک جعبهٔ اطلاعاتی فراهم کنیم که بگوید چه کسی پیشنهاد را داده و چه زمانی، و آن را از طریق [`aria-details`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-details) با پیشنهاد مرتبط کنیم:

```html
<p>
  Freida's pet is a
  <span role="suggestion" aria-details="comment-source">
    <span role="deletion">black Cat called Luna</span>
    <span role="insertion">purple T. Rex called Tiny</span></span
  >.
</p>

<div id="comment-source">
  Suggested by Chris,
  <time datetime="2019-03-30T19:29">March 30 2019, 19:29</time>
</div>
```

مرورگرها معمولاً هنگام استفاده از عناصر HTML که به‌طور ضمنی این نقش‌ها را نشان می‌دهند، یک خط خوردگی مشکی پیش‌فرض برای حذف‌ها و یک خط زیر مشکی برای درج‌ها ارائه می‌دهند. اما هنگام استفاده از نقش‌های صریح ARIA برای اصلاح عناصر HTML، مانند divها، باید از CSS برای سفارشی‌سازی ظاهر بصری این حذف‌ها و درج‌ها استفاده کنید.

## بهترین روش‌ها

### استفاده از HTML را ترجیح دهید

استفاده از عنصرهای [`<ins>`](/en-US/docs/Web/HTML/Reference/Elements/ins) و [`<del>`](/en-US/docs/Web/HTML/Reference/Elements/del) به‌طور خودکار اعلام می‌کند که یک بخش نقش `insertion` یا `deletion` دارد. در صورت امکان، استفاده از عناصر HTML را ترجیح دهید.

## مشخصات

بخشی از WAI-ARIA 1.3 خواهد بود که هنوز در حال پیش‌نویس است.
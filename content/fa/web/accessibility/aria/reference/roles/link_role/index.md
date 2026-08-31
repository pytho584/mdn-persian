---
title: "ARIA: link role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/link_role"
translated_by: "n8n + AI"
short-title: link
slug: Web/Accessibility/ARIA/Reference/Roles/link_role
page-type: aria-role
spec-urls: https://w3c.github.io/aria/#link
sidebar: accessibilitysidebar
---

یک ویجت `link` یک مرجع تعاملی به یک منبع فراهم می‌کند. منبع هدف می‌تواند خارجی یا محلی باشد؛ یعنی خارج از صفحه یا برنامه فعلی یا داخل آن.

> [!NOTE]
> در صورت امکان، توصیه می‌شود از عنصر بومی {{HTMLElement("a")}} به جای نقش `link` استفاده کنید، زیرا عناصر بومی توسط عامل‌های کاربر و فناوری کمکی پشتیبانی گسترده‌تری دارند. عناصر بومی {{HTMLElement("a")}} همچنین به طور پیش‌فرض نیازهای صفحه‌کلید و فوکوس را پشتیبانی می‌کنند، بدون نیاز به سفارشی‌سازی اضافی.

## توضیحات

نقش `link` برای شناسایی عنصری استفاده می‌شود که یک پیوند به یک منبع درون برنامه یا خارجی ایجاد می‌کند.

هنگامی که از HTML معنایی برای هدف مورد نظر استفاده نمی‌شود، ویژگی‌های تعاملی باید دوباره پیاده‌سازی شوند. به عنوان مثال، وقتی `role="link"` به یک عنصر اضافه می‌شود، کلید <kbd>tab</kbd> باید امکان دادن فوکوس به پیوند را فراهم کند و کلید <kbd>enter</kbd> باید پیوند را در هنگام فوکوس اجرا کند.

از ویژگی [`tabindex`](/en-US/docs/Web/HTML/Reference/Global_attributes/tabindex) با مقدار `0` استفاده کنید تا اطمینان حاصل شود که پیوند در ترتیب فوکوس تب صحیح قرار دارد.

> [!WARNING]
> اعمال نقش `link` به یک عنصر باعث نمی‌شود که مرورگرها آن عنصر را با ظاهر یا رفتارهای استاندارد پیوند مانند زیرخط، حلقه‌های فوکوس، پیمایش به مقصد پیوند، یا اقدامات منوی زمینه بهبود بخشند. این مسئولیت توسعه‌دهنده است.

## مثال‌ها

برای بازسازی یک پیوند قابل دسترس با استفاده از نقش `link` روی عنصری که {{HTMLElement('a')}} نیست، باید اطمینان حاصل کنید که پیوند در ترتیب تب صحیح فوکوس دریافت می‌کند، عنصر شبیه یک پیوند به نظر می‌رسد، و «پیوند» مانند یک پیوند رفتار می‌کند.

```html
<span data-href="https://mozilla.org" tabindex="0" role="link">
  Fake accessible link created using a span
</span>
```

### CSS

```css
span[role="link"] {
  color: blue;
  text-decoration: underline;
  cursor: pointer;
}
span[role="link"]:hover,
span[role="link"]:active,
span[role="link"]:focus {
  color: purple;
}

span[role="link"]:focus {
  background-color: palegoldenrod;
  outline: 1px dotted;
}
```

### JavaScript

```js
const fakeLinks = document.querySelectorAll('[role="link"]');

for (const link of fakeLinks) {
  link.addEventListener("click", navigateLink);
  link.addEventListener("keydown", navigateLink);
}

// handles click and keydown events on the link
function navigateLink(e) {
  if (e.type === "click" || e.key === "Enter") {
    const ref = e.target ?? e.srcElement;
    if (ref) {
      window.open(ref.getAttribute("data-href"), "_blank");
    }
  }
}
```

اگر عنصر با `role="link"` یک رویداد کلید <kbd>Enter</kbd> دریافت کند، این پیوند را اجرا می‌کند، به صفحه پیوند داده شده می‌رود یا فوکوس را به هدف درون صفحه منتقل می‌کند.

به صورت اختیاری، <kbd>Shift</kbd> + <kbd>F10</kbd> یک منوی زمینه برای پیوند باز می‌کند.

## بهترین روش‌ها

نقش‌های ویجت مختلف برای تعریف الگوهای تعاملی رایج استفاده می‌شوند. مشابه نقش‌های ساختار سند، برخی از این نقش‌ها، از جمله نقش `link`، معنای عناصر بومی HTML را که به خوبی پشتیبانی می‌شوند، تکرار می‌کنند و نباید استفاده شوند.

از استفاده از `link` خودداری کنید، که ما برای کامل بودن آن را گنجانده‌ایم. معادل معنایی {{HTMLElement('a')}} با قابلیت تعاملی قابل دسترس موجود و پشتیبانی شده است.

### ترجیح HTML

به جای آن از {{HTMLElement('a')}} استفاده کنید.

> [!NOTE]
> نیازی به گنجاندن `role="link"` روی یک پیوند HTML نیست زیرا `<a>` به طور پیش‌فرض آن نقش را دارد.

## مشخصات

{{Specifications}}

## همچنین ببینید

- عنصر {{HTMLElement('a')}}
- عنصر {{HTMLElement('button')}}
- [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label)
- [ARIA practices `link` role examples](https://www.w3.org/WAI/ARIA/apg/patterns/link/examples/link/)
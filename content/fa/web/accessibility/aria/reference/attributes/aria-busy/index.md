---
title: "ARIA: aria-busy attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-busy"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-busy attribute"
short-title: aria-busy
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-busy
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-busy
sidebar: accessibilitysidebar
---

ویژگی `aria-busy` یک وضعیت ARIA سراسری است که نشان می‌دهد آیا یک عنصر در حال تغییر است یا خیر.
این ویژگی به فناوری‌های کمکی کمک می‌کند تا بفهمند تغییرات محتوا هنوز کامل نشده‌اند و ممکن است بخواهند قبل از اطلاع‌رسانی به کاربران درباره به‌روزرسانی صبر کنند.
در حالی که `aria-busy` معمولاً در [مناطق زنده ARIA](/en-US/docs/Web/Accessibility/ARIA/Guides/Live_regions) استفاده می‌شود تا اعلان‌ها را تا تکمیل به‌روزرسانی‌ها به تأخیر بیندازد، می‌توان از آن در خارج از مناطق زنده نیز استفاده کرد - به عنوان مثال، در ویجت‌ها یا فیدها - برای نشان دادن تغییرات در حال انجام یا بارگذاری.

هنگامی که چندین بخش از یک منطقه زنده باید قبل از اعلام تغییرات به کاربر بارگذاری شوند، `aria-busy="true"` را تا پایان بارگذاری تنظیم کنید. سپس `aria-busy="false"` را تنظیم کنید. این کار از اعلام تغییرات توسط فناوری‌های کمکی قبل از تکمیل به‌روزرسانی‌ها جلوگیری می‌کند.

## توضیحات

بخشی از محتوا وجود دارد که به‌روزرسانی می‌شود. به‌روزرسانی‌ها مهم هستند و می‌خواهید کاربر را از تغییر آن مطلع کنید، بنابراین آن را با ویژگی [`aria-live`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-live) به یک [منطقه زنده ARIA](/en-US/docs/Web/Accessibility/ARIA/Guides/Live_regions) تبدیل کرده‌اید. ممکن است بخواهید چندین مؤلفه از آن بخش را همزمان به‌روزرسانی کنید، اما نمی‌توانید مطمئن باشید که همه چیز به طور همزمان به‌روزرسانی می‌شود. حتی اگر یک منطقه زنده بسیار مهم با `aria-live="assertive"` باشد، نمی‌خواهید با بارگذاری بخش‌های مختلف محتوا، چندین بار کاربر را قطع کنید. اینجا جایی است که `aria-busy` می‌تواند کمک کند.

ویژگی `aria-busy` یک ویژگی اختیاری مناطق زنده است که می‌تواند مقدار `true` یا `false` داشته باشد. ویژگی `aria-busy` با مقدار `true` می‌تواند به عنصری که در حال به‌روزرسانی یا تغییر است اضافه شود تا به فناوری کمکی اطلاع دهد که باید صبر کند تا تغییرات یا اصلاحات کامل شوند، سپس محتوا را به کاربر نمایش دهد. از ویژگی [`ariaBusy`](/en-US/docs/Web/API/Element/ariaBusy) شیء برای تغییر مقدار به `false` هنگامی که دانلود کامل شد استفاده کنید.

```js
ariaLiveElement.ariaBusy = "false";
```

مقدار [`aria-live`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-live) تعیین می‌کند که آیا تغییرات بلافاصله پس از تغییر مقدار به `false` اعلام می‌شوند یا فناوری کمکی تا تکمیل وظیفه فعلی صبر می‌کند و سپس کاربر را قطع می‌کند.

### درون یک `feed`

اگر یک عنصر با نقش [`feed`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/feed_role) دارای `aria-busy` تنظیم شده به `true` باشد، تغییرات رندر که در داخل فید رخ می‌دهد، به جز تغییرات آغاز شده توسط کاربر، اعلام نخواهد شد.

### درون یک `widget`

اگر تغییرات در یک ویجت رندر شده حالتی ایجاد کند که ویجت در طول اجرای اسکریپت فاقد عناصر وابسته مورد نیاز باشد، در طول فرآیند به‌روزرسانی، `aria-busy` را روی ویجت به `true` تنظیم کنید. به عنوان مثال، اگر یک درخت شبکه رندر شده چندین شاخه را به‌روزرسانی کند که لزوماً به طور همزمان رندر نمی‌شوند، جایگزینی برای جایگزینی کل درخت در یک به‌روزرسانی واحد، علامت‌گذاری درخت به عنوان مشغول در حالی که هر یک از شاخه‌ها اصلاح می‌شود، است.

## مقادیر

- false (پیش‌فرض):
  - هیچ به‌روزرسانی مورد انتظاری برای عنصر وجود ندارد.
- true
  - عنصر در حال به‌روزرسانی است.

## رابط‌های مرتبط

- {{domxref("Element.ariaBusy")}}
  - ویژگی [`ariaBusy`](/en-US/docs/Web/API/Element/ariaBusy)، بخشی از رابط هر عنصر، مقدار ویژگی `aria-busy` را منعکس می‌کند که نشان می‌دهد آیا یک عنصر در حال تغییر است.

```html
<div
  id="clock"
  role="timer"
  aria-live="polite"
  aria-atomic="true"
  aria-busy="false"></div>
```

```js
const el = document.getElementById("clock");
console.log(el.ariaBusy); // false
el.ariaBusy = "true";
console.log(el.ariaBusy); // true
```

## نقش‌های مرتبط

استفاده شده در **همه** نقش‌ها

## مشخصات

{{Specifications}}

## همچنین ببینید

- [مناطق زنده ARIA](/en-US/docs/Web/Accessibility/ARIA/Guides/Live_regions)
- [`aria-live`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-live)
- [`aria-relevant`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-relevant)
- [`aria-atomic`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-atomic)
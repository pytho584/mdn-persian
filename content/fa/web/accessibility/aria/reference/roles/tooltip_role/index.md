---
title: "ARIA: tooltip role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tooltip_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: tooltip role"
short-title: tooltip
slug: Web/Accessibility/ARIA/Reference/Roles/tooltip_role
page-type: aria-role
spec-urls: https://w3c.github.io/aria/#tooltip
sidebar: accessibilitysidebar
---

یک `tooltip` حباب متنی زمینه‌ای است که توضیحی را برای عنصری نمایش می‌دهد که با قرار گرفتن نشانگر روی آن یا فوکوس صفحه‌کلید ظاهر می‌شود.

## توضیحات

تولتیپ‌ها اطلاعات زمینه‌ای درباره یک عنصر فراهم می‌کنند زمانی که آن عنصر مالک فوکوس دریافت می‌کند یا هاور می‌شود، اما در غیر این صورت در صفحه قابل مشاهده نیست. تولتیپ به‌طور خودکار و پس از یک تأخیر کوتاه نمایش داده می‌شود؛ کاربر آن را درخواست نمی‌کند. در حالی که تولتیپ را می‌توان بر روی هر محتوایی قرار داد، اغلب نکاتی برای ابزارها یا کنترل‌ها هستند، مانند ارائه محتوای اضافی برای آیکون‌هایی که برچسب‌های کوتاه دارند (یا اصلاً برچسبی ندارند که این قابل دسترس نیست!).

تولتیپ معمولاً پس از یک تأخیر کوتاه (معمولاً یک تا پنج ثانیه) در پاسخ به هاور موس یا پس از دریافت فوکوس صفحه‌کلید توسط عنصر مالک، قابل مشاهده می‌شود. همان‌طور که بدون درخواست کاربر به‌طور خودکار باز می‌شود، با از دست رفتن فوکوس یا خروج موس نیز به‌طور خودکار بسته می‌شود. هنگامی که موس روی خود تولتیپ حرکت می‌کند باید باز بماند و همچنین باید با فشردن کلید <kbd>Escape</kbd> بسته شود.

از آنجا که خود تولتیپ هرگز فوکوس دریافت نمی‌کند و در ترتیب تب نیست، یک تولتیپ نمی‌تواند حاوی عناصر تعاملی مانند پیوندها، ورودی‌ها یا دکمه‌ها باشد.

نقش تولتیپ برای آیکون «i» اطلاعات بیشتر (ⓘ) مناسب نیست. تولتیپ مستقیماً با عنصر مالک مرتبط است. ⓘ توسط اطلاعات دقیق «توصیف نمی‌شود»؛ بلکه ابزار یا کنترل این‌گونه توصیف می‌شود.

استفاده از نقش `tooltip` در ARIA مکملی برای رفتار عادی تولتیپ مرورگر است. نمونه‌ای از تولتیپ بومی مرورگر، شیوه‌ای است که برخی مرورگرها ویژگی [`title`](/en-US/docs/Web/HTML/Reference/Global_attributes/title) عنصر را هنگام هاور طولانی موس نمایش می‌دهند. هیچ‌کس نمی‌تواند این ویژگی را از طریق فوکوس صفحه‌کلید یا تعامل لمسی فعال کند و این قابلیت را غیرقابل دسترس می‌سازد. اگر اطلاعات به اندازه‌ای مهم است که به صورت تولتیپ یا title گنجانده شود، بهتر است آن را در متن قابل مشاهده بگنجانید.

عناصر دارای نقش `tooltip` باید قبل یا هنگام نمایش تولتیپ از طریق [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby) ارجاع داده شوند. ویژگی `aria-describedby` بر روی عنصر مالک قرار دارد، نه روی تولتیپ.

تولتیپ از نظر ویژگی [`aria-haspopup`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-haspopup) بر روی عنصر مالک، پاپ‌آپ در نظر گرفته نمی‌شود، به همین دلیل در تعریف مقدماتی از «حباب متنی» استفاده کردیم.

اگرچه یک تولتیپ ممکن است ظاهر و ناپدید شود، اما چون ظاهر آن خودکار و عمداً توسط کاربر کنترل نمی‌شود، نقش [`aria-expanded`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-expanded) پشتیبانی نمی‌شود.

نام دسترس‌پذیر یک تولتیپ می‌تواند از محتوا بیاید. در تئوری، می‌تواند از [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) یا [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) بیاید، اما در بیشتر موارد، استفاده از ویژگی‌های ARIA برای ارائه نام دسترس‌پذیر به تولتیپ توصیه نمی‌شود.

تولتیپ‌ها اطلاعات اضافی ارائه می‌دهند و معمولاً تعامل مستقیمی با خود تولتیپ وجود ندارد. آن‌ها معمولاً از طریق [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby) با `id` عنصر اصلی، به محتوایی که تعریف می‌کنند مرتبط می‌شوند. بنابراین، اگر تولتیپ نام دسترس‌پذیری به صراحت تنظیم کرده باشد، آن نام به عنوان توضیحات عنصر اصلی آشکار می‌شود نه محتوای تولتیپ، که به این معنی است که محتوای تولتیپ ممکن است هرگز توسط کاربر صفحه‌خوان کشف نشود.

### نقش‌ها، حالت‌ها و ویژگی‌های مرتبط WAI-ARIA

- عنصری که به عنوان ظرف تولتیپ عمل می‌کند، دارای `role="tooltip"` است.
- عنصری که تولتیپ را فعال می‌کند، با [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby) به عنصر تولتیپ ارجاع می‌دهد.

### تعاملات صفحه‌کلید

- <kbd>Escape</kbd>
  - : تولتیپ را می‌بندد

تولتیپ باید هنگام فوکوس یا هاور شدن روی عنصر، بدون تعامل اضافی ظاهر شود. باید به‌طور خودکار ناپدید شود زمانی که فوکوس روی عنصر مالک از بین برود یا موس به خارج از عنصر مالک و تولتیپ منتقل شود. در حالی که تولتیپ فوکوس دریافت نمی‌کند، در صورت باز بودن، کلید <kbd>Escape</kbd> باید آن را ببندد.

### ویژگی‌های جاوااسکریپت مورد نیاز

- تولتیپ از طریق فوکوس صفحه‌کلید و حذف فوکوس و همچنین رویدادهای موس (حرکت موس روی عنصر و خروج موس) نمایش داده و ناپدید می‌شود.
- تولتیپ هرگز فوکوس دریافت نمی‌کند. فوکوس روی عنصر مالک می‌ماند.
- تولتیپ می‌تواند با کلید <kbd>Escape</kbd> پنهان شود.
- تولتیپ هنگام هاور شدن باز می‌ماند.
- تولتیپ فقط از طریق جاوااسکریپت و انتخابگرهای CSS پنهان می‌شود. اگر جاوااسکریپت در دسترس نباشد، تولتیپ نمایش داده می‌شود.

## مثال‌ها

```html
<label for="password">Password:</label>
<input aria-describedby="passwordrules" id="password" type="password" />
<div role="tooltip" id="passwordrules">
  <p>Password Rules:</p>
  <ul>
    <li>Minimum of 8 characters</li>
    <li>
      Include at least one lowercase letter, one uppercase letter, one number
      and one special character
    </li>
    <li>Unique to this website</li>
  </ul>
</div>
```

تولتیپ را می‌توان با CSS نمونه‌سازی کرد. نام کلاس را با جاوااسکریپت به کلاسی تغییر دهید که اگر کاربر کلید <kbd>Escape</kbd> را بزند، تولتیپ را پنهان می‌کند.

```css
[role="tooltip"] {
  visibility: hidden;
  position: absolute;
  top: 2rem;
  left: 2rem;
  background: black;
  color: white;
  padding: 0.5rem;
  border-radius: 0.25rem;
  /* Give some time before hiding so mouse can exit the input
  and enter the tooltip */
  transition: visibility 0.5s;
}
[aria-describedby]:hover,
[aria-describedby]:focus {
  position: relative;
}
[aria-describedby]:hover + [role="tooltip"],
[aria-describedby]:focus + [role="tooltip"],
[role="tooltip"]:hover,
[role="tooltip"]:focus {
  visibility: visible;
}
```

{{EmbedLiveSample("examples", "", 300)}}

مورد بالا تولتیپ را با CSS در حالت پیش‌فرض یا اگر کلاس `hide-tooltip` با جاوااسکریپت اضافه شده باشد (زمانی که کاربر <kbd>Escape</kbd> را فشار دهد)، با ویژگی اختصاصی بالا پنهان می‌کند تا اطمینان حاصل شود که تولتیپ نمایش داده نمی‌شود. وقتی عنصر مالک فوکوس دریافت می‌کند، به صورت نسبی position می‌گیرد و تولتیپ قابل مشاهده می‌شود. ما تولتیپ را هنگام هاور بر روی خود تولتیپ قابل مشاهده نگه می‌داریم که با [WCAG 1.4.13](#accessibility_concerns) سازگار است. در اینجا، با انتظار 0.5 ثانیه، اجازه می‌دهیم مکان‌نما از ورودی به تولتیپ حرکت کند بدون اینکه تولتیپ ناپدید شود؛ راه‌های دیگری نیز برای این کار وجود دارد، مانند پر کردن فاصله با یک عنصر شفاف که هنگام هاور شدن نیز تولتیپ را قابل مشاهده نگه می‌دارد.

## نگرانی‌های دسترس‌پذیری

اگر اطلاعات به اندازه‌ای مهم است که در تولتیپ قرار گیرد، آیا به اندازه‌ای مهم نیست که همیشه قابل مشاهده باشد؟

تولتیپ باید هنگام هاور شدن باز بماند، حتی اگر از نظر فنی به این معنی باشد که موس از عنصر مالک خارج می‌شود. از آنجا که محتوایی که هنگام هاور ظاهر می‌شود ممکن است درک آن دشوار یا غیرممکن باشد اگر کاربر مجبور باشد نشانگر موس را روی محرک نگه دارد، [WCAG 1.4.13](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Perceivable#guideline_1.4_make_it_easier_for_users_to_see_and_hear_content_including_separating_foreground_from_background) بیان می‌کند که محتوای قابل مشاهده باید پایدار باشد، یعنی بدون اقدام کاربر ناپدید نشود.

## بهترین روش‌ها

به جای استفاده از تولتیپ‌ها و پنهان کردن اطلاعات مهم، نوشتن توضیحات واضح، مختصر و همیشه قابل مشاهده را در نظر بگیرید. اگر فضا دارید، از تولتیپ یا toggletips استفاده نکنید. فقط برچسب‌های واضح و متن بدنه کافی ارائه دهید.

## مشخصات

{{Specifications}}

## همچنین ببینید

- [نقش `dialog`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/dialog_role)
- [CSS: شبه‌کلاس `:focus`](/en-US/docs/Web/CSS/Reference/Selectors/:focus)
- [تولتیپ‌ها و توگلتیپ‌ها](https://inclusive-components.design/tooltips-toggletips/) نوشته هیدن پیکرینگ
- [درک SC 1.4.13: محتوا در حالت هاور یا فوکوس (WCAG سطح AA)](https://www.w3.org/WAI/WCAG21/Understanding/content-on-hover-or-focus.html)
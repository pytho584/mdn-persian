---
title: "ARIA: aria-describedby attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-describedby attribute"
short-title: aria-describedby
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-describedby
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-describedby
sidebar: accessibilitysidebar
---

ویژگی سراسری `aria-describedby` عنصر (یا عناصری) را مشخص می‌کند که عنصر دارای این ویژگی را توصیف می‌کنند.

## توضیحات

ویژگی `aria-describedby` فهرستی از [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) عناصری را فهرست می‌کند که آن شیء را توصیف می‌کنند. از آن برای برقراری ارتباط بین ویجت‌ها یا گروه‌ها و متنی که آن‌ها را توصیف می‌کند استفاده می‌شود.

ویژگی `aria-describedby` محدود به کنترل‌های فرم نیست. می‌توان از آن برای مرتبط کردن متن ایستا با ویجت‌ها، گروه‌های عناصر، ناحیه‌های دارای عنوان، تعریف‌ها و موارد دیگر نیز استفاده کرد. ویژگی `aria-describedby` می‌تواند با عناصر HTML معنایی و با عناصری که دارای [`role`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles) ARIA هستند استفاده شود.

ویژگی `aria-describedby` بسیار شبیه به ویژگی [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) است. در حالی که `aria-labelledby` فهرستی از `id` برچسب‌ها یا عناصری است که ماهیت یک شیء را توصیف می‌کنند، `aria-describedby` فهرستی از `id` توصیف‌ها یا عناصری است که اطلاعات بیشتری را که کاربر ممکن است به آن نیاز داشته باشد فراهم می‌کنند. هر دو `aria-labelledby` و `aria-describedby` به عناصر دیگر ارجاع می‌دهند تا یک متن جایگزین محاسبه شود، اما یک برچسب باید مختصر باشد، در حالی که یک توصیف برای ارائه اطلاعات مفصل‌تر در نظر گرفته شده است؛ یک برچسب ماهیت یک شیء را توصیف می‌کند، در حالی که یک توصیف اطلاعات بیشتری را که کاربر ممکن است به آن نیاز داشته باشد فراهم می‌کند.

عناصری که از طریق `aria-describedby` به هم مرتبط می‌شوند نیازی به قابل مشاهده بودن ندارند. امکان ارجاع به یک عنصر حتی اگر پنهان باشد وجود دارد. برای مثال، یک کنترل فرم می‌تواند دارای توصیفی باشد که به‌طور پیش‌فرض پنهان است و در صورت درخواست با استفاده از یک ویجت افشاگر مانند آیکون «اطلاعات بیشتر» نمایش داده می‌شود. کاربران بینا برای مشاهدهٔ توصیف روی آیکون کلیک می‌کنند، در حالی که کاربران فناوری کمکی می‌توانند بلافاصله به آن دسترسی داشته باشند، زیرا توصیف از آن کنترل فرم با `aria-describedby` ارجاع شده است.

ویژگی `aria-describedby` زمانی مناسب است که محتوای مرتبط شامل متن ساده باشد. اگر محتوا گسترده باشد، معناشناسی مفیدی داشته باشد، یا ساختار پیچیده‌ای داشته باشد که نیاز به پیمایش کاربر داشته باشد، به جای آن از [`aria-details`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-details) استفاده کنید. `aria-details` به کاربران فناوری کمکی اجازه می‌دهد تا از محتوای ساختاریافته مرتبط بازدید کنند و دستورات پیمایش اضافی را فراهم می‌کند و درک ساختار یا دریافت اطلاعات در بخش‌های کوچک‌تر را آسان‌تر می‌کند.

> [!NOTE]
> محتوای `aria-describedby` باید فقط یک رشته متنی باشد. اگر معناشناسی مهم زمینه‌ای در محتوا وجود دارد، استفاده از [`aria-details`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-details) را در نظر بگیرید.

## مثال

```html
<button aria-describedby="trash-desc">Move to trash</button>
…
<p id="trash-desc">
  Items in the trash will be permanently removed after 30 days.
</p>
```

> [!NOTE]
> ویژگی `aria-describedby` برای ارجاع به توصیف‌ها از منابع خارجی طراحی نشده است. از آنجا که مقدار آن یک یا چند `id` است (در صورت چندتایی با فاصله جدا می‌شوند)، باید به عناصری در همان سند DOM ارجاع دهد.

## مقادیر

- فهرست ارجاع `ID`
  - : `id` یا فهرست جدا شده با فاصله از `id` عناصری که عنصر فعلی را توصیف می‌کنند.

## رابط‌های مرتبط

- {{domxref("Element.ariaDescribedByElements")}}
  - : ویژگی `ariaDescribedByElements` بخشی از رابط هر عنصر است.
    مقدار آن آرایه‌ای از زیرکلاس‌های {{domxref("Element")}} است که ارجاع‌های `id` موجود در ویژگی `aria-describedby` را بازتاب می‌دهد ([با برخی ملاحظات](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references)).
- {{domxref("ElementInternals.ariaDescribedByElements")}}
  - : ویژگی `ariaDescribedByElements` بخشی از رابط هر عنصر سفارشی است.
    مقدار آن آرایه‌ای از زیرکلاس‌های {{domxref("Element")}} است که ارجاع‌های `id` موجود در ویژگی `aria-describedby` را بازتاب می‌دهد ([با برخی ملاحظات](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references)).

## نقش‌های مرتبط

در **همه** نقش‌ها استفاده می‌شود. همچنین در تمام عناصر HTML قابل استفاده است.

## مشخصات

{{Specifications}}

## جستارهای وابسته

- [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby)
- [`aria-description`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-description)
- [`aria-details`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-details)
- [پشتیبانی مرورگر و فناوری کمکی از `aria-describedby`](https://a11ysupport.io/tech/aria/aria-describedby_attribute)
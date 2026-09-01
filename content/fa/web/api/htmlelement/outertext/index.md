---
title: "HTMLElement: outerText property"
short-title: outerText
slug: Web/API/HTMLElement/outerText
page-type: web-api-instance-property
browser-compat: api.HTMLElement.outerText
---

{{APIRef("DOM")}}

خاصیت **`outerText`** از رابط {{domxref("HTMLElement")}} همان مقداری را برمی‌گرداند که {{domxref("HTMLElement.innerText")}} برمی‌گرداند.
وقتی به‌عنوان setter استفاده شود، کل گره فعلی را با متن داده‌شده جایگزین می‌کند (این تفاوت با `innerText` دارد که محتوای _داخل_ گره فعلی را جایگزین می‌کند).

برای اطلاعات بیشتر و مثال‌هایی که نحوه استفاده از هر دو خاصیت را به‌عنوان getter نشان می‌دهند، به {{domxref("HTMLElement.innerText")}} مراجعه کنید.

## مقدار

یک رشته (string) که محتوای متنی رندر شده یک عنصر و عناصر فرزند آن را نشان می‌دهد.

اگر خود عنصر [در حال رندر شدن](https://html.spec.whatwg.org/multipage/rendering.html#being-rendered) نباشد (مثلاً از سند جدا شده باشد یا از دید پنهان باشد)، مقدار برگردانده‌شده همانند خاصیت {{domxref("Node.textContent")}} خواهد بود.

وقتی به‌عنوان setter استفاده شود، گره فعلی را با متن داده‌شده جایگزین می‌کند و هر خط جدید را به عنصر {{HTMLElement("br")}} تبدیل می‌کند.

## مثال‌ها

این مثال تفاوت اساسی بین `outerText` و `innerText` را هنگام استفاده به‌عنوان setter نشان می‌دهد (هنگام استفاده به‌عنوان getter آن‌ها یکسان هستند).

> [!NOTE]
> این مثال نسخه‌ای تغییر یافته از [What is the difference between innerText and outerText?](https://stackoverflow.com/questions/18481382/what-is-the-difference-between-innertext-and-outertext/18481435#18481435) (استک‌اورفلو) نوشته [codingintrigue](https://stackoverflow.com/users/571194/codingintrigue) است که تحت مجوز [CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/) منتشر شده است.

صفحه‌ای را در نظر بگیرید که HTML زیر را دارد:

```html
<div>
  <p>Original content</p>
</div>
```

`outerText` کل عنصر انتخاب‌شده را جایگزین می‌کند، بنابراین کد جاوااسکریپت `p.outerText = "Whole element replaced"` کل عنصر `p` انتخاب‌شده را جایگزین می‌کند:

```html
<div>Whole element replaced</div>
```

در مقابل، `p.innerText = "Content inside element replaced"` محتوای _داخل_ عنصر `p` انتخاب‌شده را جایگزین می‌کند:

```html
<div>
  <p>Content inside element replaced</p>
</div>
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLElement.innerText")}}
- {{domxref("Element.outerHTML")}}
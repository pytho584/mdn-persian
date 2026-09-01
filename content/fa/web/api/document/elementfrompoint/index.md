---
title: "Document: elementFromPoint() method"
short-title: elementFromPoint()
slug: Web/API/Document/elementFromPoint
page-type: web-api-instance-method
browser-compat: api.Document.elementFromPoint
---

{{APIRef("DOM")}}

متد **`elementFromPoint()`** که روی شیء {{domxref("Document")}} در دسترس است، بالاترین {{domxref("Element")}} را در مختصات مشخص‌شده (نسبت به viewport) برمی‌گرداند.

اگر عنصر در نقطه مشخص‌شده متعلق به سند دیگری باشد (مثلاً سند یک {{HTMLElement("iframe")}})، عنصر والد آن سند برگردانده می‌شود (یعنی خود `<iframe>`). اگر عنصر در نقطه داده‌شده محتوای ناشناس (anonymous) یا تولیدشده توسط XBL باشد، مانند نوارهای پیمایش یک جعبه متنی، اولین عنصر جد ancestor غیرناشناس (مثلاً همان جعبه متنی) برگردانده می‌شود.

عناصری که {{cssxref("pointer-events")}} آن‌ها روی `none` تنظیم شده باشد نادیده گرفته می‌شوند و عنصر زیرین آن‌ها برگردانده می‌شود.

اگر متد روی سند دیگری اجرا شود (مثلاً زیرسند یک `<iframe>`)، مختصات نسبت به سندی که متد روی آن فراخوانی می‌شود سنجیده می‌شوند.

اگر نقطه مشخص‌شده خارج از محدوده قابل مشاهده سند باشد یا هر یک از مختصات منفی باشد، نتیجه `null` است.

اگر نیاز به یافتن موقعیت دقیق داخل عنصر دارید، از {{domxref("Document.caretPositionFromPoint()")}} استفاده کنید.

## Syntax

```js-nolint
elementFromPoint(x, y)
```

### پارامترها

- `x`
  - : مختصات افقی یک نقطه، نسبت به لبه چپ {{Glossary("viewport")}} جاری.
- `y`
  - : مختصات عمودی یک نقطه، نسبت به لبه بالای viewport جاری.

### مقدار بازگشتی

بالاترین شیء {{domxref("Element")}} واقع در مختصات مشخص‌شده.

## مثال‌ها

این مثال دو دکمه ایجاد می‌کند که به شما امکان می‌دهند رنگ فعلی عنصر پاراگراف واقع در مختصات `(2, 2)` را تنظیم کنید.

### HTML

```html
<p id="para1">Some text here</p>
<button>Blue</button>
<button>Red</button>
```

HTML شامل پاراگرافی است که رنگ آن تغییر می‌کند و همچنین دو دکمه: یکی برای تغییر رنگ به آبی و دیگری برای تغییر رنگ به قرمز.

### JavaScript

```js
function changeColor(newColor) {
  const elem = document.elementFromPoint(2, 2);
  elem.style.color = newColor;
}

document.querySelectorAll("button").forEach((button) => {
  button.addEventListener("click", (event) => {
    changeColor(event.target.textContent.toLowerCase());
  });
});
```

متد `changeColor()` عنصر واقع در نقطه مشخص‌شده را به دست می‌آورد و سپس ویژگی {{cssxref("color")}} فعلی آن عنصر را به رنگی که در پارامتر `newColor` مشخص شده تنظیم می‌کند.

### نتیجه

{{EmbedLiveSample('Examples', 400, 120)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Document.elementsFromPoint()")}}
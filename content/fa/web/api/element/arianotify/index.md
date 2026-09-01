---
title: "Element: ariaNotify() method"
---

---
title: "Element: ariaNotify() method"
short-title: ariaNotify()
slug: Web/API/Element/ariaNotify
page-type: web-api-instance-method
browser-compat: api.Element.ariaNotify
---

{{ApiRef("DOM")}}

متد **`ariaNotify()`** از رابط {{domxref("Element")}} یک رشتهٔ متنی را برای اعلان توسط {{glossary("screen reader")}} (صفحه‌خوان) در صف قرار می‌دهد.

## سینتکس

```js-nolint
ariaNotify(announcement)
ariaNotify(announcement, options)
```

### پارامترها

- `announcement`
  - : رشته‌ای که متنی را که باید اعلان شود مشخص می‌کند.
- `options` {{optional_inline}}
  - : یک شیء گزینه‌ها که شامل ویژگی‌های زیر است:
    - `priority`
      - : یک مقدار شمارشی که اولویت اعلان را مشخص می‌کند. مقادیر ممکن عبارت‌اند از:
        - `normal`
          - : اعلان اولویت عادی دارد. پس از هر اعلانی که صفحه‌خوان در حال حاضر در حال بیان آن است، گفته می‌شود. این مقدار پیش‌فرض است.
        - `high`
          - : اعلان اولویت بالا دارد. بلافاصله گفته می‌شود و هر اعلانی را که صفحه‌خوان در حال حاضر در حال بیان آن است قطع می‌کند.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## توضیحات

متد **`ariaNotify()`** می‌تواند یک اعلان صفحه‌خوان را به‌صورت برنامه‌نویسی‌شده فعال کند. این متد عملکردی مشابه [مناطق زنده ARIA](/en-US/docs/Web/Accessibility/ARIA/Guides/Live_regions) را فراهم می‌کند، با این مزایا:

- مناطق زنده فقط پس از تغییرات در DOM می‌توانند اعلان صادر کنند، در حالی که یک اعلان `ariaNotify()` می‌تواند در هر زمانی صادر شود.
- اعلان‌های مناطق زنده شامل خواندن محتوای به‌روزشدهٔ گرهٔ DOM تغییر یافته هستند، در حالی که محتوای اعلان `ariaNotify()` می‌تواند مستقل از محتوای DOM تعریف شود.

توسعه‌دهندگان اغلب محدودیت‌های مناطق زنده را با استفاده از گره‌های DOM پنهانی که مناطق زنده روی آن‌ها تنظیم شده است دور می‌زنند و محتوای آن‌ها با محتوایی که باید اعلان شود به‌روزرسانی می‌شود. این کار ناکارآمد و مستعد خطا است و `ariaNotify()` راهی برای اجتناب از چنین مسائلی فراهم می‌کند.

برخی صفحه‌خوان‌ها چندین اعلان `ariaNotify()` را به ترتیب می‌خوانند، اما این موضوع در همهٔ صفحه‌خوان‌ها و پلتفرم‌ها تضمین نمی‌شود. معمولاً فقط آخرین اعلان گفته می‌شود. ترکیب چند اعلان در یک اعلان، مطمئن‌تر است.

برای مثال، فراخوانی‌های زیر:

```js
elemRef.ariaNotify("Hello there.");
elemRef.ariaNotify("The time is now 8 o'clock.");
```

بهتر است به این صورت ترکیب شوند:

```js
elemRef.ariaNotify("Hello there. The time is now 8 o'clock.");
```

یک فراخوانی `ariaNotify()` می‌تواند روی هر عنصری در DOM انجام شود، به‌جز عناصری که مرورگر آن‌ها را برای دسترس‌پذیری «جالب» در نظر نمی‌گیرد و هنگام ساخت درخت دسترس‌پذیری نادیده می‌گیرد. اینکه دقیقاً کدام عناصر نادیده گرفته می‌شوند در مرورگرهای مختلف متفاوت است، اما فهرست معمولاً شامل عناصر کانتینری با ارزش معنایی کم یا بدون ارزش معنایی است، مانند عناصر {{htmlelement("html")}} و {{htmlelement("body")}}.

اعلان‌های `ariaNotify()` به {{glossary("transient activation")}} (فعال‌سازی گذرا) نیاز ندارند؛ باید مراقب باشید که کاربران صفحه‌خوان را با تعداد زیادی اعلان بمباران نکنید، زیرا این کار می‌تواند تجربهٔ کاربری بدی ایجاد کند.

### اولویت‌های اعلان

یک اعلان `ariaNotify()` با `priority: high` قبل از یک اعلان `ariaNotify()` با `priority: normal` اعلان می‌شود.

اعلان‌های `ariaNotify()` تقریباً معادل اعلان‌های منطقهٔ زندهٔ ARIA به شرح زیر هستند:

- `ariaNotify()` با `priority: high`: معادل `aria-live="assertive"`.
- `ariaNotify()` با `priority: normal`: معادل `aria-live="polite"`.

با این حال، اعلان‌های `aria-live` نسبت به اعلان‌های `ariaNotify()` اولویت خواهند داشت.

### انتخاب زبان

صفحه‌خوان‌ها صدای مناسب برای خواندن اعلان‌های `ariaNotify()` (از نظر لهجه، تلفظ و غیره) را بر اساس زبان مشخص‌شده در ویژگی [`lang`](/en-US/docs/Web/HTML/Reference/Global_attributes/lang) عنصر انتخاب می‌کنند؛ یا اگر عنصر ویژگی `lang` مشخصی نداشته باشد، از ویژگی `lang` تنظیم‌شده روی نزدیک‌ترین جد آن استفاده می‌کنند. اگر هیچ ویژگی `lang` در HTML مشخص نشده باشد، زبان پیش‌فرض user agent (عامل کاربر) استفاده می‌شود.

### یکپارچه‌سازی با Permissions Policy

استفاده از `ariaNotify()` در یک سند یا {{htmlelement("iframe")}} می‌تواند توسط [Permission Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) به نام {{httpheader("Permissions-Policy/aria-notify", "aria-notify")}} کنترل شود.

به‌طور خاص، در مواردی که یک خط‌مشی تعریف‌شده استفاده را مسدود کند، هر اعلانی که با استفاده از `ariaNotify()` ایجاد شده باشد بی‌صدا با شکست مواجه می‌شود (یعنی ارسال نخواهد شد).

## مثال‌ها

برای یک مثال کامل‌تر، [مثال فهرست خرید دسترس‌پذیر](/en-US/docs/Web/API/Document/ariaNotify#accessible_shopping_list_example) را در صفحهٔ {{domxref("Document.ariaNotify()")}} ببینید. اگر `ariaNotify()` را روی یک ارجاع به عنصر فراخوانی کنید نه روی شیء `Document`، این مثال دقیقاً به همان شکل کار می‌کند.

### استفادهٔ پایه از `ariaNotify()`

این مثال شامل یک {{htmlelement("button")}} (دکمه) است که هنگام کلیک، یک اعلان صفحه‌خوان را روی خودش فعال می‌کند.

```html live-sample___basic-arianotify
<button>Press</button>
```

```css hidden live-sample___basic-arianotify
html,
body {
  height: 100%;
}

body {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

```js live-sample___basic-arianotify
document.querySelector("button").addEventListener("click", () => {
  document.querySelector("button").ariaNotify("You ain't seen me, right?");
});
```

#### نتیجه

خروجی به این صورت است:

{{EmbedLiveSample("basic-arianotify", "100%", 60, , , , "aria-notify")}}

سعی کنید یک صفحه‌خوان را فعال کنید و سپس دکمه را فشار دهید. باید بشنوید که صفحه‌خوان این عبارت را بیان می‌کند: "You ain't seen me, right?" (تو من را ندیده‌ای، درست است؟)

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Document.ariaNotify()")}}
- [مناطق زنده ARIA](/en-US/docs/Web/Accessibility/ARIA/Guides/Live_regions)
---
title: "FontFaceSet: check() method"
short-title: check()
slug: Web/API/FontFaceSet/check
page-type: web-api-instance-method
browser-compat: api.FontFaceSet.check
---

{{APIRef("CSS Font Loading API")}}{{AvailableInWorkers}}

متد `check()` از {{domxref("FontFaceSet")}} مقدار `true` برمی‌گرداند اگر بتوانید متنی را با استفاده از مشخصات فونت داده‌شده رندر کنید، بدون آنکه تلاشی برای استفاده از فونت‌هایی در این `FontFaceSet` شود که هنوز به‌طور کامل بارگذاری نشده‌اند. این یعنی می‌توانید از مشخصات فونت بدون ایجاد [تعویض فونت](/en-US/docs/Web/CSS/Reference/At-rules/@font-face/font-display) استفاده کنید.

> [!NOTE]
> متد `check()` برای تأیید اینکه آیا یک سبک فونت خاص قابل رندر است یا یک فونت خاص به‌طور کامل بارگذاری شده است طراحی نشده است. در عوض، اگر متن مشخص‌شده با استفاده از مشخصات فونت داده‌شده بدون ایجاد تعویض فونت قابل رندر باشد، `true` برمی‌گرداند. این بدان معناست که حتی اگر فونت درخواستی موجود یا به‌طور کامل بارگذاری نشده باشد، متد ممکن است همچنان `true` برگرداند. این رفتار به جلوگیری از مشکلات بصری مرتبط با تعویض فونت کمک می‌کند، اما اگر در تلاش برای تأیید در دسترس بودن یک فونت خاص هستید، ممکن است غیرشهودی به نظر برسد.

## سینتکس

```js-nolint
check(font)
check(font, text)
```

### پارامترها

- `font`
  - : یک مشخصات فونت با استفاده از سینتکس ویژگی {{cssxref("font")}} در CSS، برای مثال `"italic bold 16px Roboto"`
- `text` {{optional_inline}}
  - : چهره‌های فونت (font faces) را به آن‌هایی محدود می‌کند که محدوده یونیکدشان حداقل یکی از کاراکترهای موجود در text را شامل شود. این [پوشش گلیف‌های منفرد را بررسی نمی‌کند](https://lists.w3.org/Archives/Public/www-style/2015Aug/0330.html). پیش‌فرض آن رشته‌ای متشکل از یک کاراکتر فاصله (`" "`) است.

### مقدار برگشتی

یک مقدار {{jsxref("Boolean")}} که اگر رندر کردن متن با مشخصات فونت داده‌شده تلاشی برای استفاده از هیچ‌یک از فونت‌های این `FontFaceSet` که هنوز به‌طور کامل بارگذاری نشده‌اند نکند، `true` است.

این بدان معناست که همه فونت‌های موجود در این `FontFaceSet` که با مشخصات فونت داده‌شده مطابقت دارند، ویژگی [`status`](/en-US/docs/Web/API/FontFace/status) آن‌ها روی `"loaded"` تنظیم شده است.

در غیر این صورت، این تابع `false` برمی‌گرداند.

## مثال‌ها

در مثال زیر، یک `FontFace` جدید می‌سازیم و آن را به `FontFaceSet` اضافه می‌کنیم:

```js
const font = new FontFace("molot", 'url("/shared-assets/fonts/molot.woff2")', {
  style: "normal",
  weight: "400",
  stretch: "condensed",
});

document.fonts.add(font);
```

### فونت‌های بارگذاری‌نشده

فونت هنوز بارگذاری نشده است، بنابراین `check("12px molot")` مقدار `false` برمی‌گرداند و نشان می‌دهد که اگر سعی کنیم از مشخصات فونت داده‌شده استفاده کنیم، بارگذاری فونت را آغاز خواهیم کرد:

```js
console.log(document.fonts.check("12px molot"));
// false: the matching font is in the set, but is not yet loaded
```

### فونت‌های سیستمی

اگر فقط یک فونت سیستمی را در آرگومان `check()` مشخص کنیم، `true` برمی‌گرداند، زیرا می‌توانیم از فونت سیستمی بدون بارگذاری هیچ فونتی از مجموعه استفاده کنیم:

```js
console.log(document.fonts.check("12px Courier"));
// true: the matching font is a system font
```

### فونت‌های ناموجود

اگر فونتی را مشخص کنیم که در `FontFaceSet` نیست و فونت سیستمی هم نیست، `check()` مقدار `true` برمی‌گرداند، زیرا در این وضعیت به هیچ فونتی از مجموعه وابسته نخواهیم بود:

```js
console.log(document.fonts.check("12px i-dont-exist"));
// true: the matching font is a nonexistent font
```

### فونت‌های سیستمی و بارگذاری‌نشده

اگر هم یک فونت سیستمی و هم فونتی در مجموعه که هنوز بارگذاری نشده را مشخص کنیم، `check()` مقدار `false` برمی‌گرداند:

```js
console.log(document.fonts.check("12px molot, Courier"));
// false: `molot` is in the set but not yet loaded
```

### فونت‌های در حال بارگذاری

اگر فونتی از مجموعه را مشخص کنیم که هنوز در حال بارگذاری است، `check()` مقدار `false` برمی‌گرداند:

```js
function check() {
  font.load();
  console.log(document.fonts.check("12px molot"));
  // false: font is still loading
  console.log(font.status);
  // "loading"
}

check();
```

### فونت‌های بارگذاری‌شده

اگر فونتی از مجموعه را مشخص کنیم که بارگذاری شده است، `check()` مقدار `true` برمی‌گرداند:

```js
async function check() {
  await font.load();
  console.log(document.fonts.check("12px molot"));
  // true: font has finished loading
  console.log(font.status);
  // "loaded"
}

check();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}